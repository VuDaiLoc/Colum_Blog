---
title: "Bài 3: Hàm"
date: 2025-05-18T15:00:00+07:00
draft: true
tags: ["Java", "Cơ bản", "Fuction"]
categories: ["Java"]
cover: "images2/java.webp"
description: "Đóng gói logic vào phương thức để tái sử dụng, giảm lặp code và tổ chức chương trình rõ ràng."
---

## Giới thiệu
Phương thức (method) là khối lệnh thực hiện một nhiệm vụ cụ thể. Dùng phương thức giúp **tái sử dụng code**, **giảm lặp**, **dễ kiểm thử** và **dễ bảo trì**. Bài này tổng hợp cú pháp, phạm vi biến, quá tải (overload), tham số, giá trị trả về và ví dụ thực hành.

---

## Giải thích chi tiết

### Cú pháp tổng quát
```java
<modifiers> <KiểuTrảVề> <tenPhuongThuc>(<DanhSáchThamSố>) {
    // thân phương thức
    // ...
    // return <giá trị>; // nếu không phải void
}
```

- modifiers thường gặp: `public, private, protected, static, final`
- KiểuTrảVề: `void` (không trả về) hoặc kiểu bất kỳ (`int, double, String`, lớp tự định nghĩa…).
- DanhSáchThamSố: có thể rỗng hoặc nhiều tham số, cách nhau bởi dấu phẩy.

---

### Ví dụ cụ thể 
Ví dụ 1: Hàm tính bình phương (static) và lời gọi
```java 
public class DemoFunction {
    public static int binhPhuong(int x) {
        return x * x;
    }

    public static void main(String[] args) {
        int a = 5;
        int bp = binhPhuong(a);
        System.out.println("Bình phương của " + a + " là " + bp);
    }
}
```

Ví dụ 2: Hàm `void` có tham số — chào người dùng
```java
public class Greeting {
    static void chaoHoi(String ten, int namSinh) {
        int tuoi = 2025 - namSinh;
        System.out.println("Xin chào " + ten + ". Năm nay bạn " + tuoi + " tuổi.");
    }

    public static void main(String[] args) {
        chaoHoi("An", 2000);
        chaoHoi("Bình", 1995);
    }
}
```

---

