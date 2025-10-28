---
Title: "Bài 5: Mảng trong Java"
date: 2025-06-10T15:00:00+07:00
draft: true
tags: ["Java", "Cơ bản", "Array"]
categories: ["Java"]
cover: "images2/java.webp"
description: "Tìm hiểu cách khai báo, khởi tạo và duyệt mảng trong Java. Học cách sử dụng thuộc tính length, mảng nhiều chiều và các thao tác phổ biến như tìm min, max, đảo mảng."
---

## Giới thiệu
Mảng (Array) là cấu trúc dữ liệu giúp lưu trữ **nhiều giá trị cùng kiểu dữ liệu** trong một biến duy nhất.  
Thay vì tạo hàng chục biến riêng lẻ, ta có thể gộp chúng vào một mảng.  
Việc hiểu rõ mảng là nền tảng để học tiếp các cấu trúc dữ liệu phức tạp hơn như danh sách (List), tập hợp (Set), hay bản đồ (Map).

---

## Giải thích chi tiết

### Khai báo mảng
Cú pháp tổng quát:
```java
<kiểu_dữ_liệu>[] <tên_mảng>;
// hoặc
<kiểu_dữ_liệu> <tên_mảng>[];
```

Ví dụ: 
```java
int[] arr;      // khai báo mảng số nguyên
String[] names; // khai báo mảng chuỗi
```

### Khởi tạo mảng
Có thể cấp phát kích thước (số phần tử) hoặc khởi tạo trực tiếp:
```java 
arr = new int[5];             // tạo mảng 5 phần tử (mặc định = 0)
String[] colors = {"Red", "Blue", "Green"}; // khởi tạo trực tiếp
```

### Truy cập phần tử
Chỉ số mảng bắt đầu từ 0.
```java 
arr = new int[5];             // tạo mảng 5 phần tử (mặc định = 0)
String[] colors = {"Red", "Blue", "Green"}; // khởi tạo trực tiếp
```

### Thuộc tính `length`
Để biết số phần tử trong mảng, dùng:
```java
System.out.println(arr.length);
```

### Duyệt mảng
Dùng vòng lặp `for` hoặc `for-each`:
```java 
for (int i = 0; i < arr.length; i++) {
    System.out.println(arr[i]);
}

// hoặc
for (int value : arr) {
    System.out.println(value);
}
```

---

## Ví dụ minh họa 
### Ví dụ 1: Tính điểm trung bình của sinh viên
```java 
public class DiemTrungBinh {
    public static void main(String[] args) {
        double[] scores = {8.5, 7.2, 9.0, 6.8, 8.0};
        double sum = 0;
        for (int i = 0; i < scores.length; i++) {
            sum += scores[i];
        }
        double avg = sum / scores.length;
        System.out.println("Điểm trung bình: " + avg);
    }
}
```

### Ví dụ 2: Tìm phần tử lớn nhất và nhỏ nhất
```java 
public class TimMinMax {
    public static void main(String[] args) {
        int[] nums = {12, 5, 7, 20, 3};
        int min = nums[0];
        int max = nums[0];

        for (int n : nums) {
            if (n < min) min = n;
            if (n > max) max = n;
        }

        System.out.println("Giá trị nhỏ nhất: " + min);
        System.out.println("Giá trị lớn nhất: " + max);
    }
}
```



