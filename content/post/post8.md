---
title: "Bài 8: Cấu trúc điều khiển trong JavaScript"
date: 2025-07-14T15:00:00+07:00
draft: true
tags: ["JavaScript","Cơ bản", "Control Flow"]
categories: ["JavaScript"]
cover: "images2/javas.webp"
description: "Tìm hiểu cách điều khiển luồng chương trình bằng if, else, switch, for, while, do...while và break/continue trong JavaScript. Minh họa bằng ví dụ thực tế và bài tập."
---

## Giới thiệu
Cấu trúc điều khiển (Control Flow) cho phép bạn **ra quyết định và lặp lại hành động** trong chương trình.  
JavaScript cung cấp các cấu trúc quen thuộc như `if...else`, `switch`, `for`, `while`, `do...while`, cùng các từ khóa điều khiển vòng lặp `break`, `continue`.  
Việc hiểu rõ chúng là nền tảng để bạn viết chương trình linh hoạt, xử lý điều kiện và dữ liệu hiệu quả hơn.

---

## Giải thích chi tiết

### Cấu trúc rẽ nhánh `if`, `else if`, `else`
```javascript
let age = 20;

if (age < 18) {
  console.log("Chưa đủ tuổi");
} else if (age < 60) {
  console.log("Người trưởng thành");
} else {
  console.log("Người cao tuổi");
}
```
Lưu ý: JavaScript cho phép if lồng nhau, nhưng nên tránh lồng quá sâu để dễ đọc hơn.

### Cấu trúc switch...case  
Dùng khi có nhiều nhánh điều kiện so sánh bằng (===).
```javascript
let day = 3;
let name;

switch (day) {
  case 1: name = "Thứ Hai"; break;
  case 2: name = "Thứ Ba"; break;
  case 3: name = "Thứ Tư"; break;
  case 4: name = "Thứ Năm"; break;
  case 5: name = "Thứ Sáu"; break;
  default: name = "Cuối tuần";
}

console.log("Hôm nay là:", name);
```
Dùng break để tránh rơi xuống các case tiếp theo.
Có thể gom nhiều case chung một xử lý:
```javascript
switch (day) {
  case 6:
  case 7:
    console.log("Cuối tuần");
    break;
  default:
    console.log("Ngày thường");
}
```

### Vòng lặp `for`
Dùng khi biết số lần lặp.
```javascript
for (let i = 1; i <= 5; i++) {
  console.log("Lần lặp:", i);
}
```
Cú pháp tổng quát:
```javascript
for (khởi_tạo; điều_kiện; cập_nhật) { ... }
```

### Vòng lặp `while`
Chạy khi điều kiện còn đúng, thích hợp khi chưa biết trước số lần lặp.
```javascript
let n = 1;
while (n <= 3) {
  console.log("Giá trị n:", n);
  n++;
}
```

### Vòng lặp `do...white`
Chạy ít nhất 1 lần, rồi mới kiểm tra điều kiện.
```javascript
let count = 1;
do {
  console.log("Lặp lần:", count);
  count++;
} while (count <= 3);
```

### Break và Continue
`break`: dừng vòng lặp ngay lập tức.
`continue`: bỏ qua lượt hiện tại, tiếp tục vòng lặp sau.
```javascript
for (let i = 1; i <= 5; i++) {
  if (i === 3) continue; // bỏ qua 3
  if (i === 5) break;    // dừng khi gặp 5
  console.log(i);
}
```

### Vòng lặp lồng nhau
```javascript
for (let i = 1; i <= 3; i++) {
  for (let j = 1; j <= 2; j++) {
    console.log(`i=${i}, j=${j}`);
  }
}
```

### Vòng lặp for...of và for...in
| Cấu trúc | Dùng cho | Ví dụ | Kết quả |
|:--------:|:---------|:------|:--------|
| `for...of` | Duyệt giá trị trong mảng, chuỗi | `for (let x of [1,2,3])` | 1,2,3|
| `for...in` | Duyệt tên thuộc tính của object | `for (let k in {a:1,b:2})` | a,b |

Ví dụ: 
```javascript
const person = { name: "An", age: 20 };
for (let key in person) {
  console.log(key, ":", person[key]);
}
```

---

## Ví dụ minh họa
### Ví dụ 1: Duyệt mảng sinh viên và lọc theo điều kiện
```javascript
const students = [
  { name: "An", score: 8.2 },
  { name: "Bình", score: 6.5 },
  { name: "Chi", score: 9.1 },
];

for (let s of students) {
  if (s.score < 7) continue; // bỏ qua sinh viên điểm thấp
  console.log(s.name, "-", s.score);
}
```
### Ví dụ 2: Kiểm tra số nguyên tố
```javascript
let n = 7;
let isPrime = true;

if (n < 2) isPrime = false;
else {
  for (let i = 2; i <= Math.sqrt(n); i++) {
    if (n % i === 0) {
      isPrime = false;
      break;
    }
  }
}
console.log(isPrime ? "Là số nguyên tố" : "Không phải số nguyên tố");
```