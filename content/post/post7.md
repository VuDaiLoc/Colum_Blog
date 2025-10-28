---
title: "Bài 7: Toán tử và Biểu thức trong JavaScript"
date: 2025-06-17T15:00:00+07:00
draft: true
tags: ["JavaScript","Cơ bản", "Operators"]
categories: ["JavaScript"]
cover: "images2/javas.webp"
description: "Tổng hợp các loại toán tử trong JavaScript: số học, gán, so sánh, logic, điều kiện, typeof, nullish coalescing, spread/rest và các ví dụ minh họa cụ thể."
---

## Giới thiệu
Toán tử (operator) là ký hiệu hoặc từ khóa giúp **thực hiện phép tính hoặc thao tác** trên dữ liệu.  
Trong JavaScript, biểu thức (expression) là **một đoạn code trả về giá trị** — ví dụ `3 + 5`, `"Hello" + "World"`, `a > b`, `true && false`.  
Hiểu rõ cách hoạt động của toán tử giúp bạn tránh lỗi logic và viết code ngắn gọn, hiệu quả hơn.

---

## Giải thích chi tiết

### Toán tử số học (Arithmetic)
```javascript
let a = 10, b = 3;
console.log(a + b); // 13  cộng
console.log(a - b); // 7   trừ
console.log(a * b); // 30  nhân
console.log(a / b); // 3.333...
console.log(a % b); // 1   chia lấy dư
console.log(a ** b); // 1000  lũy thừa (ES6)
```
### Toán tử gán (Assignment)
```javascript
let x = 5;
x += 2; // x = x + 2 → 7
x -= 1; // 6
x *= 3; // 18
x /= 2; // 9
x %= 4; // 1
```
### Toán tử so sánh (Comparison)
| Toán tử | Ý nghĩa | Ví dụ | Kết quả |
|:-------:|:--------|:------|:--------|
| `==` | So sánh bằng *(ép kiểu)* | `5 == "5"` | `true` |
| `===` | So sánh bằng *(nghiêm ngặt)* | `5 === "5"` | `false` |
| `!=` | Khác *(ép kiểu)* | `5 != "5"` | `false` |
| `!==` | Khác *(nghiêm ngặt)* | `5 !== "5"` | `true` |
| `<`, `>`, `<=`, `>=` | So sánh số hoặc chuỗi | `"a" < "b"` | `true` |

### Toán tử logic (Logical)
```javascript
let a = true, b = false;
console.log(a && b); // false (AND)
console.log(a || b); // true  (OR)
console.log(!a);     // false (NOT)

// Ngoài ra, JavaScript còn hỗ trợ Short-circuit evaluation:

console.log(false && "JS"); // false
console.log(true  || "JS"); // true
```

### Toán tử điều kiện (Ternary)
Cú pháp: 
```javascript 
điều_kiện ? giá_trị_nếu_true : giá_trị_nếu_false
```
Ví dụ:
```javascript
let age = 20;
let type = age >= 18 ? "Người lớn" : "Trẻ em";
console.log(type); // "Người lớn"
```

### Toán tử typeof, delete, in, instanceof
```javascript
let obj = { name: "An", age: 22 };
console.log(typeof obj);         // "object"
console.log("name" in obj);      // true
delete obj.age;                  // xóa thuộc tính
console.log(obj);                // { name: "An" }

function User() {}
let u = new User();
console.log(u instanceof User);  // true
```

### Toán tử nullish coalescing (??)
Dùng để cung cấp giá trị mặc định khi biến là null hoặc undefined.
```javascript
let name = null;
let displayName = name ?? "Guest";
console.log(displayName); // "Guest"
```
Khác với `||` ở chỗ `??` chỉ kiểm tra null/undefined, không xem `0`, `""` là falsy.

### Toán tử spread (...) và rest
`Spread`: sao chép/gộp mảng, object
`Rest`: gom nhiều đối số thành mảng.
```javascript
// spread
let arr1 = [1,2,3];
let arr2 = [...arr1, 4,5];
console.log(arr2); // [1,2,3,4,5]

// rest
function sum(...nums) {
  return nums.reduce((a,b) => a + b, 0);
}
console.log(sum(1,2,3,4)); // 10
```

### Toán tử chuỗi (String concatenation)
```javascript 
let name = "Linh";
console.log("Xin chào " + name + "!");     // cổ điển
console.log(`Xin chào ${name}!`);          // template literal (ES6)
```

---

## Ví dụ minh họa
### Ví dụ 1: Tổng hợp các phép tính cơ bản
```javascript
let a = 8, b = 3;
console.log("a + b =", a + b);
console.log("a - b =", a - b);
console.log("a * b =", a * b);
console.log("a / b =", a / b);
console.log("a % b =", a % b);
```

### Ví dụ 2: Dùng toán tử logic để rút gọn điều kiện
```javascript
let isAdmin = true;
let name = "Thành";

isAdmin && console.log(`Xin chào Admin ${name}`);
// tương đương:
if (isAdmin) console.log(`Xin chào Admin ${name}`);
```