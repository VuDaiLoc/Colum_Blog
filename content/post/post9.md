---
title: "Bài 9 - Hàm mũi tên (Arrow Function), Callback và Scope trong JavaScript"
date: 2025-10-14T15:00:00+07:00
draft: true
tags: ["JavaScript","Cơ bản", "Function"]
categories: ["JavaScript"]
cover: "images2/javas.webp"
description: "Hiểu rõ cú pháp hàm mũi tên (arrow function), hàm callback, phạm vi biến (scope), và từ khóa this trong JavaScript qua ví dụ thực tế và lỗi thường gặp."
---

## Giới thiệu
Hàm (function) là **trái tim của JavaScript**.  
Từ ES6, JavaScript giới thiệu cú pháp mới là **Arrow Function (=>)** giúp code ngắn gọn, dễ đọc hơn.  
Bên cạnh đó, bạn cần hiểu **callback function**, **scope (phạm vi biến)** và hành vi của **`this`** để tránh lỗi phổ biến khi viết JS hiện đại.

---

## Giải thích chi tiết

### Hàm truyền thống và hàm mũi tên
**Hàm truyền thống:**
```javascript
function add(a, b) {
  return a + b;
}
```
**Hàm mũi tên**
```javascript
const add = (a, b) => a + b;
```
Khi thân hàm chỉ có một biểu thức, có thể bỏ dấu {} và từ khóa return.
Nếu có nhiều lệnh, cần {} và return như bình thường.
```javascript
const greet = name => {
  const message = `Xin chào, ${name}!`;
  return message;
};
```

### So sánh funcion và => Arrow Function
| Đặc điểm | `function` truyền thống | `=>` Arrow Function |
|:--------:|:------------------------|:--------------------|
| Cú pháp | Dài hơn | Ngắn gọn |
| Có `this` riêng | Có | Không (kế thừa `this` từ phạm vi cha) |
| Dùng làm constructor (`new`) | Có thể | Không thể |
| Có `arguments` | Có | Không có  (phải dùng rest `...args`) |

**Ví dụ**
```javascript
function normal() { console.log(this); } // this = object gọi hàm
const arrow = () => console.log(this);   // this = phạm vi bên ngoài

const obj = { name: "A", show: normal, show2: arrow };
obj.show();  // this = obj
obj.show2(); // this = window (hoặc undefined trong strict mode)
```

### Hàm callback
Callback là hàm được truyền vào hàm khác như một tham số để gọi lại khi cần.
```javascript
function xinChao(callback) {
  console.log("Xin chào buổi sáng!");
  callback();
}

function tamBiet() {
  console.log("Hẹn gặp lại!");
}

xinChao(tamBiet);
```

### Scope (Phạm vi biến)
Có 3 loại chính:
- 1. Global scope: biến khai báo ngoài hàm → dùng mọi nơi.
- 2. Function scope: khai báo bằng var trong hàm → chỉ tồn tại trong hàm.
- 3. Block scope: khai báo bằng let, const → chỉ tồn tại trong {}.

**Ví dụ:**
```javascript
let x = 10; // global

function test() {
  var y = 5;  // function scope
  if (true) {
    let z = 2; // block scope
    console.log(x + y + z); // 17
  }
  // console.log(z); // lỗi: z is not defined
}
test();
```

### Từ khóa this trong Arrow Function
Arrow function không có this riêng, mà kế thừa từ phạm vi cha.
```javascript
const person = {
  name: "An",
  sayHello: function() {
    setTimeout(function() {
      console.log("Xin chào, tôi là " + this.name); // ❌ undefined
    }, 1000);
  }
};
person.sayHello();
```
Giải pháp: dùng arrow function để kế thừa this:
```javascript
const person2 = {
  name: "An",
  sayHello() {
    setTimeout(() => {
      console.log("Xin chào, tôi là " + this.name); // ✅ hoạt động
    }, 1000);
  }
};
person2.sayHello();
```

### Hàm lồng hàm và closure
Closure là khi hàm con có thể truy cập biến của hàm cha, ngay cả khi hàm cha đã kết thúc.
```javascript
function outer() {
  let count = 0;
  return function() {
    count++;
    console.log("Số lần gọi:", count);
  };
}

const click = outer();
click(); // Số lần gọi: 1
click(); // Số lần gọi: 2
```
→ count vẫn được lưu trong bộ nhớ nhờ closure, không bị mất.

---

## Ví dụ minh họa
### Ví dụ 1: Callback với forEach
```javascript
const fruits = ["Táo", "Cam", "Chuối"];
fruits.forEach((f, i) => console.log(`${i + 1}. ${f}`));
```

### Ví dụ 2: Closure tạo bộ đếm
```javascript
function createCounter() {
  let count = 0;
  return () => ++count;
}

const counter = createCounter();
console.log(counter()); // 1
console.log(counter()); // 2
console.log(counter()); // 3
```