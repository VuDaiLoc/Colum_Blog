---
title: "Bài 6: Biến và Kiểu dữ liệu trong JavaScript"
publishDate: 2025-06-14T15:00:00+07:00
draft: true
tags: ["JavaScript", "Cơ bản"]
categories: ["JavaScript"]
cover: "images2/javas.webp"
description: "Phân biệt let/const/var, các kiểu dữ liệu cơ bản, typeof, so sánh == và ===, và các lưu ý về phạm vi, hoisting, và truthy/falsy trong JavaScript."
---

## Giới thiệu
JavaScript là ngôn ngữ **kiểu động** (dynamic typing): một biến có thể nhận nhiều kiểu giá trị khác nhau tại các thời điểm khác nhau.  
Để viết JS an toàn và ít lỗi, bạn cần nắm vững: `let`, `const`, `var`; các **kiểu dữ liệu**, phép **so sánh nghiêm ngặt** `===`, toán tử `typeof`, và khái niệm **truthy/falsy**.

---

## Giải thích chi tiết

### Khai báo biến: let, const, var
```javascript
let age = 25;      // phạm vi khối (block scope), có thể gán lại
const PI = 3.14;   // phạm vi khối, KHÔNG gán lại (nhưng có thể mutate object/array)
var name = "An";   // phạm vi hàm/toàn cục (function/global), hoisting (nên hạn chế dùng)
```
### Kiểu dữ liệu cơ bản
Primitives: `number, string, boolean, null, undefined, bigint, symbol`

Non-primitive: `object (bao gồm Array, Function, Date, …)`

Kiểm tra kiểu: 
```javascript
typeof 123            // "number"
typeof "abc"          // "string"
typeof true           // "boolean"
typeof undefined      // "undefined"
typeof null           // "object"   <-- lịch sử của JS (quirk)
typeof {a:1}          // "object"
typeof [1,2,3]        // "object"   // Array là object
typeof function(){}   // "function"
```

### Ép kiểu, truthy/falsy
Falsy: false, 0, -0, 0n, "" (chuỗi rỗng), null, undefined, NaN

Mọi giá trị khác đều truthy.
```javascript
if ("")   console.log("truthy"); else console.log("falsy"); // falsy
if ("0")  console.log("truthy"); else console.log("falsy"); // truthy
```

### So sánh `==` và `===`
`==` ép kiểu trước khi so sánh.

`===` không ép kiểu (khuyến nghị dùng).
```javascript
5 == "5"   // true
5 === "5"  // false
null == undefined   // true
null === undefined  // false
```

### Phạm vi & hoisting
```javascript
if (true) {
  let x = 1;   // chỉ tồn tại trong block
  var y = 2;   // tồn tại ngoài block (trong cùng function/global)
}
// console.log(x); // ReferenceError
console.log(y);     // 2

console.log(a); // undefined (hoisting biến var)
var a = 10;

// console.log(b); // ReferenceError (let/const không hoisted theo cách dùng được)
let b = 5;
```

---

## Ví dụ minh họa
### Ví dụ 1: Minh họa thay đổi kiểu động và typeof
```javascript
let v;
console.log(typeof v); // "undefined"

v = 10;
console.log(typeof v); // "number"

v = "mười";
console.log(typeof v); // "string"

v = {ten: "An", tuoi: 20};
console.log(typeof v); // "object"
```

### Ví dụ 2: So sánh và ép kiểu
```javascript
console.log(0 == false);   // true (ép kiểu)
console.log(0 === false);  // false
console.log(" \t\n" == 0); // true (chuỗi whitespace -> 0)
console.log("5" + 3);      // "53" (nối chuỗi)
console.log("5" - 3);      // 2   (ép sang number)
```