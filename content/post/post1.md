---
title: "Bài 1: Biến và kiểu dữ liệu trong Java"
date: 2025-05-10T15:00:00+07:00
draft: true
tags: ["Java", "Cơ bản"]
categories: ["Java"]
cover: "images2/java.webp"
description: "Tìm hiểu cách khai báo biến và các kiểu dữ liệu trong Java — nền tảng đầu tiên giúp bạn quản lý và thao tác dữ liệu chính xác."
---


## Giới thiệu
Biến và kiểu dữ liệu là nền tảng cơ bản của mọi ngôn ngữ lập trình.  
Biến dùng để lưu trữ giá trị, còn kiểu dữ liệu xác định dạng của giá trị đó (số, chuỗi ký tự, logic đúng/sai, v.v.).  
Đối với người mới học Java, hiểu cách khai báo biến và các kiểu dữ liệu giúp xây dựng những chương trình đơn giản đầu tiên.  
Chủ đề này quan trọng vì đây là bước khởi đầu để bạn quản lý và thao tác dữ liệu trong mã nguồn một cách chính xác và hiệu quả.

---

## Giải thích chi tiết
Java là ngôn ngữ kiểu tĩnh, nghĩa là mỗi biến phải được khai báo với một kiểu dữ liệu cố định ngay từ đầu.  
Một số kiểu dữ liệu cơ bản (primitive) trong Java gồm:

- `int`: số nguyên (ví dụ 1, 2, 3…)
- `double`: số thực dấu phẩy động (ví dụ 3.14)
- `char`: một ký tự đơn (ví dụ `'A'`)
- `boolean`: giá trị logic `true` hoặc `false`

Ngoài ra, Java có các kiểu đối tượng như `String` (chuỗi ký tự) và nhiều kiểu khác.  
Mỗi kiểu dữ liệu chiếm một lượng bộ nhớ nhất định và có phạm vi giá trị khác nhau.  
Ví dụ: `int` lưu khoảng từ -2 tỷ đến 2 tỷ, còn `long` có phạm vi lớn hơn nhiều.

Cú pháp khai báo biến:
```java
<kiểu_dữ_liệu> <tên_biến>;
```

---

## Ví dụ chi tiết
```java
public class ViDuBien {
    public static void main(String[] args) {
        // Khai báo và khởi tạo biến
        int soNguyen = 10;            // kiểu int  
        double soThuc = 3.14;         // kiểu double  
        char kyTu = 'A';              // kiểu char  
        boolean laSinhVien = true;    // kiểu boolean  
        String thongDiep = "Xin chào!"; // kiểu chuỗi (String)

        // Sử dụng biến: in giá trị ra màn hình
        System.out.println("soNguyen = " + soNguyen);
        System.out.println("soThuc = " + soThuc);
        System.out.println("kyTu = " + kyTu);
        System.out.println("laSinhVien = " + laSinhVien);
        System.out.println("thongDiep = " + thongDiep);
    }
}
```



