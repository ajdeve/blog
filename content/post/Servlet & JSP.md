---
title: "Servlet & JSP"
date: 2021-01-17T11:30:03+00:00
weight: 1
aliases: ["/web"]
tags: ["Web"]
categories: ["Web"]
series: ["Web"]
author: "Me"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
disableShare: false
comments: true
---

## Servlet & JSP  
### 정의
**Servlet:** 서블렛은 Java class로서 서버의 요청을 다루기 위해 쓰인다. 

 - 서블렛을 통해 사용자의 input을 모으거나, DB에서 레코드를 출력한다거나 dynamic web page들을 생성하거나 할
   수 있다
  - 쉽게 말하면 "클라이언트의 요구를 받아 그에 대한 처리를 한 후, 결과를 되돌려주는 서버 모듈"이다. 
  - **서블릿은 JSP에서 컨텐츠와 비즈니스 로직을 분리**한다.   JSP가 텍스트 파일 구조인데 비해 서블릿은 자바 클래스 구조이다.

  
출처: [https://ddo-o.tistory.com/77](https://ddo-o.tistory.com/77) [공순이 블로그]
  

#### Servlet 돌아가는 과정 
![enter image description here](https://t1.daumcdn.net/cfile/tistory/99977D405C50873F03)
 ***서블렛은 Servlet Container (서블렛 컨테이너)에게서 컨트롤된다. 서버가 요청을 받을때 서버가 요청을 서블렛 컨테이너에게 넘겨주고, 서블렛 컨테이너가 요청을 처리하기 위한 서블렛에게 전달한다.*** 
 
 1. Client가 웹 서버에 요청을 보낸다.  
 2. 서버가 요청을 받고 서블렛 컨테이너가 HttpServletRequest, HttpServletResponse 두 객체를 생성한다. 
 3. 서블렛 컨테이너가 가 해당 담당하는 서블렛으로 요청을 보낸다. 
 4. 서블렛이 요청을 process하고 응답을 생성한다. (컨테이너가 서블렛 service() 메소드를 호출해서 POST, GET여부에 따라 doGet() 또는 doPost()를 호출하여 동적인 페이지를 생성함, 
 5. 서블렛이 웹 서버에 HttpServletResponse 객체에 응답을 보낸다. 
 6. 서버가 응답을 client에게 다시 보내고 client 브라우저는 스크린에 출력한다. 그리고 HttpServletResponse & Request 객체를 소멸시킨다.  

### Servlet  Life Cycle 
![Servlet Life Cycle-Servlet and JSP tutorial- Edureka](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2019/01/2-2.png)

 1. 서블렛 로딩: 서버가 시작할때 모든 서블렛을 로딩한다. 
 2. 서블렛 시작: init() 메소드로 서블렛이 시작함
 ```java
 public void init() throws ServletException { // Initialization code like set up database etc.... }
 ```
 3. 요청 처리: service() 메소드로 client의 요청을 처리하며 서블렛에게 client의 요청을 알린다. 
 ```java
 public void service(ServletRequest request, ServletResponse response) throws ServletException, IOException { // ... }
 ```
 4. 서블렛을 종료: destroy() 메소드로 서블렛이 종료됨.  서블렛의 라이프 사이클에서 단 한번 실행됨 
 ```java
 public void destroy() { // }
 ```

* init()과 destroy() 메소드는 한번 실행됨 

### JSP: Java Server Page
**정의:** Java 언어를 기반으로 하는 Server Side 스크립트 언어

 - 자바 서버 페이지는 서블렛과 같이 웹앱을 만들기위한 기술이며, JSTL등등 다양한 표현법을 사용해서 더 많은 기능을 구현할 수 있다. 
 - 서버쪽의 기술 
 - JSP tag 는 JAVA 코드를 HTML 페이지에 넣을때 사용한다. 
 - HTML 코드에 Java 코드를 넣어 동적인 웹 페이지를 생성하는 웹 어플리케이션 도구
 - JSP는 JSP 컨테이너에 의해서 client 요청을 처리하기전에 servlet으로 변환된다. 
 - Servlet 기술의 확장
 - Servlet를 보완한 스크립트 방식 표준
 - Servlet의 모든 기능 + 추가적인 기능

#### JSP Life Cycle 
![enter image description here](https://www.guru99.com/images/2/022220_0728_ServletvsJS2.png)

 1. JSP를 서블렛으로 변환한다. 
 2. JSP 페이지를 컴파일한다. 
 3. _jsp.java 가 class file_jsp.class로 변환된다. 
 4. Object of generated servlet is created. 
 5. _jspinit() 메소드가 컨테이너로 시작된다. 
 6. _jspservice() 메소드가 컨테이너에 의해 요청을 처리한다. 
 7. _jspDestroy() 메소드가 실행되어 컨테이너에 의해 종료된다. 

![](https://t1.daumcdn.net/cfile/tistory/247AC8445459E2E203)

## Code Example 

1.  **Declaration Tag** :-메서드와 변수 모두 선언할 수 있다.  
``java
**Syntax:-** 
<%!  Dec var  %>
**Example:-**
<%! int var=10; %>
 ``

2.  **Java Scriplets** :- 임의의 자바코드 대부분은 여기 가능하다. Method가 아닌 변수만 선언할 수 있다. 
``java
 **Syntax:-** 
<% java code %>
``

3.  **JSP Expression** :- String으로 변환되어 Servlet의 출력에 삽입된다. 끝에 ";" 세미콜론을 붙이지 않는다.  
``java
 **Syntax:-** 
<%= expression %> 
 **Example:-** 
<% num1 = num1+num2 %> 
``

4.  **JAVA Comments** :-주석달기 
``java
 **Syntax:-** 
<% -- JSP Comments %>
``

5.  **JAVA Comments** :-주석달기 
``java
 **Syntax:-** 
<% -- JSP Comments %>
``

6. **JAVA Directive** : -JSP 페이지의 전체적인 구조에 영향을 미친다. 전체 구조에 대해 WAS에 지시를 내린다. 지시어에 들어가는 것: page, include, taglib
``java
<%@ directive %>
``
![enter image description here](https://gmlwjd9405.github.io/images/web/jsp-directive-example.png)

**page:** page 지시어는 Container에 명령을 제공하는데 사용된다.
```java
<%@ page attribute = "value" %>
```
**include**: include 지시어는 변환 단계에서 다른 외부 파일의 내용을 현재 JSP에 병합하도록 Container에 지시한다.
```java 
<%@ include file = "relative_url" %>
```
**taglib:** JSP API를 사용하면 HTML 또는 XML 태그처럼 보이는 사용자 정의 태그(custom tags)를 정의할 수 있다. tag library는 사용자가 정의한 동작을 구현한 사용자 정의(user-defined) 태그 집합이다. 
```java
<%@ taglib uri = "uri" prefix = "prefixOfTag" %>
```
7. **JSP Action** 
JSP Action XML 구문 안의 구조들을 사용하여 WAS의 동작을 제어한다.
``<jsp:forward>`` action
다른 리소스(JSP, html 또는 Servlet과 같은 정적 페이지)로 요청을 전달하는데 사용한다.
``<jsp:include> ``action
현재 JSP 페이지에 다른 리소스를 포함시키는데 사용한다.
``<jsp:useBean>`` action
해당하는 Bean(자바 객체)이 이미 존재하는지 확인한다.
객체가 없으면 지정된 객체를 생성한다.
``<jsp:setProperty>`` action
Bean(자바 객체)의 속성을 설정한다.
``<jsp:getProperty>`` action
주어진 속성값을 가져오는데 사용되며 이를 문자열로 변환하고 동적인 웹 페이지를 생성하는데 해당 내용을 사용할 수 있다.

용도
1) 동적으로 파일을 삽입하고
2) JavaBeans 구성 요소를 재사용하고
3) 사용자를 다른 페이지로 전달(forward)할 수 있다.
https://gmlwjd9405.github.io/2018/11/03/jsp.html

![enter image description here](https://gmlwjd9405.github.io/images/web/jsp-action-example.png)

7. **JSP EL (Explression Language)** 
```java
<%-- JSP 2.0(Preferred)  --%>
<ul>
  <li>Name: ${customer.name}</li>
  <li>Email: ${customer.email}</li>  
  <li>ID: ${customer.id}</li>
</ul> 
```
8. **JSP JSTL **
JSP Scriptlet에서 JSTL로! 
``` java
<html>
<head>
<title>Count to 10 in JSP scriptlet</title>
</head>
<body>
   <%
      for(int i=1;i<=10;i++){
   %>
   <%=i%><br/>
   <%
      }
   %>
</body>
</html>
```
```java
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c"%>
<html>
<head>
<title>Count to 10 Example (using JSTL)</title>
</head>
<body>
   <c:forEach var="i" begin="1" end="10" step="1">
      <c:out value="${i}"/>
      <br/>
   </c:forEach>
</body>
</html>
```

### 차이점
기능은 동일하나 역할은 다르다. 
|Servlet  | JSP |
|--|--|
|JAVA code | html 기반 code |
| MVC 구조의 Controller 역할 | MVC 구조의 View 역할  |
| JSP 보다 빠름 | JSP 는 JSP를 자바 코드로 번역하는 과정을 먼저 거치고 컴파일이 필요해서 Servlet보다 느림  |
| 모든 protocol 요청을 받음 | http 요청만 받음  |
| 주된 업무는 client에게 정보를 입력받아 적절한 HTML문서를 돌려주는 역할. |  JSP는 실행시키면 이 문서가 자동적으로 서블렛으로 컴파일 되어서 실행됨|


### Request & Response
#### HttpServletRequest
- 사용자가 서버로 보낸 요청: Request
 - http프로토콜의 request정보를 서블렛에게 전다하는 목적으로 사용됨
 - 헤더정보, 파라미터, 쿠키, URL등의 정보를 읽고 처리하는 메소드를 가지고 있음 
 - body의 stream을 읽어 들이는 메소드를 가지고 있음 

| 메소드 | 설명 |
|--|--|
|getParameter(?) | 요청에 담긴 값을 반환 |
|getAttribute(?) | 요청의 속성 값 가져오기 |
|getAttribute(?) | 요청의 속성 값 추가 |
|request.getCookies() | 쿠키에 대한 정보 |
|request.getSession() | 세션에 대한 정보|
|request.getRequestDispatcher() |*|
* RequestDispatcher는 클라이언트로부터 최초에 들어온 요청을 JSP/Servlet 내에서 원하는 자원으로 요청을 넘기는(보내는) 역할을 수행하거나, 특정 자원에 처리를 요청하고 처리 결과를 얻어오는 기능을 수행하는 클래스입니다.  
  
출처: [https://dololak.tistory.com/502](https://dololak.tistory.com/502) [코끼리를 냉장고에 넣는 방법]


#### HttpServletResponse
- 웹서버의 응답: Response
- Servlet Container.는 어떤 client가 요청을 보냈는지 알고 있고 해당 client에게 응답을 보내기 위한 HttpServletResponse객체를 생성해서 서블렛에 전달한다. 
- 서블렛은 해당 객체를 이용해 content type, 응답코드, 응답 메세지등을 전송한다. 
-  JSP를 활용할 경우, JSP 페이지의 실행 결과를 웹 브라우저에 되돌려 줄 때 사용하는 객체 

| 메소드 | 설명 |
|--|--|
|PrintWriter getWriter() | 응답에 char data를 보내기 위한 방법 |
|setContentType(String) | MIME 타입 지정및 글자의 인코딩 지정 |
|response.SendRedirect(url) | 웹 서버가 웹 브라우저에게 지정한 페이지로 이동하도록 지시|



### Servlet Code Example 
```java
package step01.method;

import java.io.IOException;

import javax.servlet.Servlet;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
/*
 * client가 요청하는 url값 설정 annotation
 * https://ip:port/project명/[directory]/file명.html
 * https://ip:port/project명/[directory]/servletURL매핑값
 * http://localhost/step01_basic/encore01
 * encore01 -> alias 
 */
@WebServlet("/encore01")
public class Servlet01Method extends HttpServlet implements Servlet {
	//get 방식 요청시 자동 호출되는 메소드 
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		System.out.println("doGet()");
		//client가 입력한 데이터 획득 - 문자열 간주 <input type="text" name="id"><br>
		String id = request.getParameter("id"); //무조건 반환 타입이 String입니다. id key 자체가 없을 경우 null값 반환
		String pw = request.getParameter("pw");
		
//		//접속한 client한테 한글 응답
//		//mime type & 한글 응답이 가능한 설정
//		response.setContentType("text/html;charset=utf-8");
//		PrintWriter out =response.getWriter();
		
		if(id.equals("SMITH") && pw.equals("11")) {
			//forward
			request.getRequestDispatcher("success").forward(request, response);
		}else {
			//redirect
			response.sendRedirect("fail");
		}
	}	
	//post 방식 요청시 자동 호출되는 메소드 
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		System.out.println("doPost*()");
		
		//요청 객체에 한글이 포함되어 있을 경우 깨짐 현상 방지를 위한 설정
			request.setCharacterEncoding("utf-8");
			System.out.println(request.getParameter("name"));
		String id = request.getParameter("id"); //무조건 반환 타입이 String입니다. id key 자체가 없을 경우 null값 반환
		String pw = request.getParameter("pw");
		
		if(id.equals("SMITH") && pw.equals("11")) {
			//forward
			request.getRequestDispatcher("success").forward(request, response);
		}else {
			//redirect
			response.sendRedirect("fail");
		}
	
	}

}
```
```java
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Web Form Test</title>
</head>
<body>
	<h2>이름과 성을 입력하세요.</h2>

	<form action="encore01" method = "post">
  	<label for="fname">아이디:</label><br>
  	<input type="text" name="id"><br>
  	<label for="lname">비밀번호:</label><br>
  	<input type="password" name="pw"><br><br>
  	이름 : <input type="text" name="name"><br>
  	<input type="submit" value="로그인">
	</form> 

</body>
</html>
 ```
 
