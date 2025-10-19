---
title: "Bài 4: Lập trình hướng đối tượng (OOP) cơ bản trong Java"
date: 2025-05-29T15:00:00+07:00
draft: true
tags: ["Java","Cơ bản", "OOP"]
categories: ["Java"]
cover: "images2/java.webp"
description: "Nắm các khái niệm class, object, đóng gói (encapsulation), kế thừa (inheritance), đa hình (polymorphism) và ví dụ thực hành trong Java."
---

## Giới thiệu 
Lập trình hướng đối tượng (OOP) giúp tổ chức chương trình theo **lớp (class)** và **đối tượng (object)**, phản ánh thực thể ở đời thực bằng **thuộc tính (fields)** và **hành vi (methods)**.  
Bốn trụ cột chính: **đóng gói** (encapsulation), **kế thừa** (inheritance), **đa hình** (polymorphism) và **trừu tượng** (abstraction). Bài này tập trung vào 3 trụ cột đầu + ví dụ thực hành.

---

## Giải thích chi tiết

### Class và Object
- **Class**: bản thiết kế mô tả thuộc tính & hành vi.
- **Object**: thể hiện cụ thể class, được tạo bằng `new`.

```java 
class SinhVien {
    String ten;
    int tuoi;

    void gioiThieu() {
        System.out.println("Tôi là " + ten + ", " + tuoi + " tuổi.");
    }
}
```

### Tạo đối tượng:
```java 
SinhVien sv = new SinhVien();
sv.ten = "An";
sv.tuoi = 20;
sv.gioiThieu();
```

### Đóng gói (Encapsulation):
Ẩn chi tiết bên trong đối tượng; thuộc tính để private, truy cập qua `getter/setter.`
``` java
class Account {
    private String owner;
    private double balance;

    public Account(String owner, double balance) {
        this.owner = owner;
        this.balance = balance;
    }
    public String getOwner() { return owner; }
    public double getBalance() { return balance; }

    public void deposit(double amount) {
        if (amount > 0) balance += amount;
    }
    public boolean withdraw(double amount) {
        if (amount > 0 && amount <= balance) { balance -= amount; return true; }
        return false;
    }
}
```

### Kế thừa (Inheritance)
Lớp con `extends` lớp cha để tái sử dụng và mở rộng hành vi.
```java 
class Animal {
    public void sound() { System.out.println("Some sound"); }
}

class Dog extends Animal {
    @Override
    public void sound() { System.out.println("Woof!"); }
}
```

### Đa hình (Polymorphism)
Gọi phương thức qua tham chiếu lớp cha nhưng chạy phiên bản của `lớp con (override).`
```java 
Animal a = new Dog();
a.sound(); // Woof!
```

---

## Ví dụ minh họa:
Ví dụ 1: Đóng gói + khởi tạo qua constructor
```java
public class DemoEncapsulation {
    public static void main(String[] args) {
        Account acc = new Account("Alice", 1000);
        acc.deposit(250.5);
        boolean ok = acc.withdraw(500);
        System.out.println("Chủ TK: " + acc.getOwner());
        System.out.println("Rút thành công? " + ok);
        System.out.println("Số dư: " + acc.getBalance());
    }
}
```

Ví dụ 2: Kế thừa + ghi đè (override) + từ khóa `super`
```java 
class Person {
    protected String name;
    public Person(String name) { this.name = name; }
    public String info() { return "Person: " + name; }
}

class Student extends Person {
    private String mssv;
    public Student(String name, String mssv) {
        super(name);           // gọi constructor lớp cha
        this.mssv = mssv;
    }
    @Override
    public String info() {     // ghi đè
        return "Student: " + name + " - MSSV: " + mssv;
    }
}

public class DemoInheritance {
    public static void main(String[] args) {
        Person p = new Person("Bình");
        Person s = new Student("An", "SE12345"); // đa hình
        System.out.println(p.info());
        System.out.println(s.info());            // gọi phiên bản Student.info()
    }
}
```

