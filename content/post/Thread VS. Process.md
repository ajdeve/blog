---
title: "Thread VS. Process"
date: 2021-01-12T11:30:03+00:00
weight: 1
aliases: ["/DS"]
tags: ["DS"]
categories: ["DS"]
series: ["DS"]
author: "Me"
showToc: true
TocOpen: false
draft: false
hidemeta: false
disableShare: false
comments: false
---
## Thread VS. Process 
**Thread VS. Process**
프로세스는 독립적이며 프로세스 안에는 스레드가 있다. 
프로세스에게 주어진 메모리는 공유가 가능하지 않으면 프로세스 안에 있는 스레드들은 자원과 메모리를 공유한다. 

### 정의
[스레드와-프로세스](https://velog.io/@ditt/%EC%8A%A4%EB%A0%88%EB%93%9C%EC%99%80-%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4)

### 특이점
- Process는 서로 소통하지 않지만 IPC(Inter Process Communication) 라는게 존재한다
- JAVA에는 프로세스라는게 존재하지 않는다, Java.exe 자체가 프로세스다. 
- 프로세스라는 것은 프로그램과 같은 개념으로 볼 수 있다. 
- 동시다발적으로 요청을 처리하기 위해 스레드를 사용할 수 있다. 

### 이해도 향상을 위한 그림 
![Java Thread](https://www.tutorialspoint.com/java/images/Thread_Life_Cycle.jpg)

### 코드 예시 

```java
public class MyThread extends Thread {
    public void run(){
       System.out.println("MyThread running");
    }
  }
  
```
```java
	MyThread myThread = new MyThread();
	  myTread.start();
  ```
  
OR 
```java
Thread thread = new Thread(){
    public void run(){
      System.out.println("Thread Running");
    }
  }

  thread.start();
```

Thread 스타트로 소환된 thread에서 run이 실행될때 "Thread Running"이 출력됨
