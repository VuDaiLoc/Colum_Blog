---
title: "Bài 2: Vòng lặp trong Java"
date: 2025-05-14T15:00:00+07:00
draft: true
tags: ["Java", "Cơ bản", "Loop"]
categories: ["Java"]
cover: "images2/java.webp"
description: "Hiểu và sử dụng các loại vòng lặp trong Java như for, while, do-while và for-each để duyệt dữ liệu hiệu quả và tránh lỗi logic."
---

## Giới thiệu
Vòng lặp là một trong những cấu trúc điều khiển cơ bản của lập trình,  
cho phép **thực thi lặp lại một đoạn mã nhiều lần** cho đến khi một điều kiện nào đó không còn đúng.  
Việc hiểu và sử dụng đúng vòng lặp giúp lập trình viên tránh trùng lặp mã nguồn,  
viết chương trình ngắn gọn, dễ bảo trì và dễ mở rộng hơn.

Trong Java có bốn loại vòng lặp chính:
- `for`
- `while`
- `do...while`
- `for-each` (vòng lặp mở rộng dành cho mảng và danh sách)

---

## Giải thích chi tiết

###  Vòng lặp `for`
Dùng khi **biết trước số lần lặp**.

Cú pháp:
```java
for (khởi_tạo; điều_kiện; cập_nhật) {
    // thân vòng lặp
}
```
Ví dụ:
```java
for (int i = 1; i <= 5; i++) {
    System.out.println("Lần lặp thứ " + i);
}
```

### Vòng lặp `while`
Dùng khi **chưa biết trước số lần lặp**, chỉ cần điều kiện đúng thì lặp tiếp

Cú pháp:
```java
while (điều_kiện) {
    // thân vòng lặp
}
```
Ví dụ:
```java
int n = 1;
while (n <= 5) {
    System.out.println("Giá trị n: " + n);
    n++;
}
```

### Vòng lặp do...while 
Khác `while` ở chỗ `thân vòng lặp được chạy ít nhất 1 lần`, rồi mới kiểm tra điều kiện

Cú pháp:
```java
do {
    // thân vòng lặp
} while (điều_kiện);
```
Ví dụ: 
```java
int dem = 1;
do {
    System.out.println("Lần lặp: " + dem);
    dem++;
} while (dem <= 3);
```

### Vòng lặp for-each
Dùng để `duyệt qua từng phần tử của mảng` hoặc danh sách mà `không cần chỉ số`

Ví dụ:
```java
int[] numbers = {1, 2, 3, 4, 5};

for (int num : numbers) {
    System.out.println("Giá trị: " + num);
}
```

---