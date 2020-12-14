---
title: "JAVA Method Examples"
date: 2020-09-15T11:30:03+00:00
weight: 1
aliases: ["/java1"]
tags: ["JAVA"]
categories: ["JAVA"]
series: ["JAVA"]
author: "Me"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
disableShare: false
comments: false
---

## JAVA

### Level 1. 기초 메서드

#### 1. System.out 활용 메서드

##### - 출력

```java
public static void main(String[] args) {
        System.out.print("Hello World");
    }
```

##### - String 출력

```java
public static void main(String[] args) {
        String h = "Hello World";
        System.out.print(h);
    }
```

##### - String + 출력

```java
public static void main(String[] args) {
        String a = "Hello";
        String b = " ";
        String c = "World";
        System.out.print(a + b + c);
    }
```

##### - String 출력 +, ++, if, ==

```java
public static void main(String[] args) {
        String a = "Hello";
        String b = " ";
        String c = "World";

        int i = 1;
        i++;
        
        if (i == 2) {
            System.out.println(a + b + c);
        }else {
            System.out.println(b);
        }
    }
```

#### 2. charAt 활용 메서드

##### - 출력 charAt, for, ++, String

```java
public static void main(String[] args) {
        
    String java = "Hello World!";
    
    for(int i = 0; i < java.length(); i++) {
    char character = java.charAt(i);
        
    System.out.print(character);
}

```

#### 3. class 활용 메서드

##### - Class +, new

```java
class A{
    String a = "Hello world!";
}

public class ExampleSet {
    
    public static void main(String[] args) {
        A a = new A();  
        System.out.println(a.a);
    }
}
```

##### - Class +, new, +

```java
class B{
    String b = "Hello ";
}

class C{
    String c = "world!";
}

public class ExampleSet {

    public static void main(String[] args) {
        B b = new B();
        C c = new C();
        System.out.println(b.b + c.c);
    }
}
```

##### - Class +, Array, new, +

```java
class D {
    String[] d = { "Hello ", "world!" };
}

public class ExampleSet {
    
    public static void main(String[] args) {
        D d = new D();
        System.out.println(d.d[0] + d.d[1]);
    }
}
```

