---
title: "Spring Framework"
date: 2021-01-26T11:30:03+00:00
weight: 1
aliases: ["/spring"]
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
comments: false
---

# Spring Framework


![spring framework tutorial](https://static.javatpoint.com/images/spimages/spring1.png)


> Rod Johnson이 2003년 개발한 Spring Framework는 JavaEE 앱을 쉽게 만들게 한다. 
> 객체를 한곳에서 모아서 관리하며 표준화와 정형화된 코드를 짤 수 있게 하는 프레임워크이다.
> 
> Spring Framework + Business Logic (컨텐츠) = Application 

## Spring Framework란?

- 자바 플랫폼을 위한 오픈소스 애플리케이션 프레임워크로서 **엔터프라이즈급** 애플리케이션을 개발하기 위한 모든 기능을 종합적으로 제공하는 **경량급 애플리케이션 프레임워크** 
- **Spirng Framework는 경량 컨테이너로 자바 객체를 담고 직접 관리**한다.  객체의 생성 및 소멸 그리고 라이프 사이클을관리하며 언제든 Spring 컨테이너로 부터 필요한 객체를 가져와 사용할 수 있다.
- 우리나라의 공공기관의 웹 서비스 개발 시 사용을 권장하고 있는 **전자정부 표준프레임워크**의 기반 기술로서 쓰이고 있다.  
- 표준화가 되어있는 코드를 통해서 어떤 개발자가 봐도 해결할 수 있게 한다. 
- 객체를 한곳에서 모아서 관리하며 표준화와 정형화된 코드를 짤 수 있게 하는 프레임워크
  
# 주요 특징

##  1. 경량 컨테이너(크기와 부하의 측면)로서 자바 객체를 직접 관리

각각의 객체 생성, 소멸과 같은 라이프 사이클을 관리하며 스프링으로부터 필요한 객체를 얻어올 수 있다. 돈도 적게 들어감. 

##  2. 제어 역행 (IoC : Inversion of Control)

컨트롤의 제어권이 사용자가 아니라 프레임워크에 있어 필요에 따라 **스프링에서** 사용자의 코드를 호출한다.

###   Spring은 IOC (Inversion of Control 제어의 역전) 기반의 Framework이다. 

***이전의 프로그램***
객체 결정 및 생성 -> 의존성 객체 생성 -> 객채 내의 메소드 호출 하는 작업을 반복했다. 이는 각 객체들이 프로그램의 흐름을 결정하고 각 객체를 구성하는 작업에 직접적으로 참여한 것이다.

**즉, 모든 작업을 사용자가 제어하는 구조인 것**이였는데 IOC에서는  객체는 자기가 사용할 객체를 선택하거나 생성하지 않는다. 또한 자신이 어디서 만들어지고 어떻게 사용되는지 또한 모른다. 자신의 모든 권한을 다른 대상에 위임함으로 써 제어권한을 위임받은 특별한 객체에 의해 결정되고 만들어진다.

**즉, 제어의 흐름을 사용자가 컨트롤 하지 않고 위임한 특별한 객체에 모든 것을 맡기는 구조**

 ### Spring은 IOC 컨테이너이다. 
 빈 객체의 생성(new), 빈 객체간 관계 설정(set), 빈 객체 관리(singleton등) 가 컨테이너 주요기능 으로 Spring Container가 관리한다. 

### IOC의 구성요소 
#### DL: Dependency Lookup 
**의존성 검색:** 컨테이너에서는 객체들을 관리하기 위해 별도의 저장소에 빈을 저장하는데 저장소에 저장되어 있는 개발자들이 컨테이너에서 제공하는 API 를 이용하여 사용하고자 하는 빈 을 검색하는 방법

#### DI: Dependency Injection (제일 중요한 컨셉중 하나) 
**의존성 주입:** 의존성 주입이란 객체가 서로 의존하는 관계가 되게 의존성을 주입하는 것이며 객체지향 프로그램에서 의존성 이란 하나의 객체가 어떠한 다른 객체를 사용하고 있음을 의미한다. 그리고 객체는 의존하고 있는 객체를 코드 상에서 직접 생성하고나 검색할 필요가 없다. 

IOC에서의 DI란 바로  **각 클래스 사이에 필요로 하는 의존관계를 빈 설정 정보를 바탕으로 컨테이너가 자동으로 연결**해 주는 것이다. 

[출처](https://khj93.tistory.com/entry/Spring-Spring-Framework%EB%9E%80-%EA%B8%B0%EB%B3%B8-%EA%B0%9C%EB%85%90-%ED%95%B5%EC%8B%AC-%EC%A0%95%EB%A6%AC)


##  3. 의존성 주입 (DI  : Dependency Injection)

- 각각의 계층이나 서비스들 간에 의존성이 존재할 경우 프레임워크가 서로 연결시켜준다.

원래 코드
```java
public  class Store { 
private Item item; 
public Store() {
 item = new ItemImpl1(); 
 } 
 }
```

DI 코드 
```java
public  class Store { 
private Item item; 
public Store(Item item) {
 this.item = item; 
 } }
```

https://www.javaguides.net/2018/06/guide-to-dependency-injection-in-spring.html

##  4. 관점지향 프로그래밍 (AOP : Aspect-Oriented Programming)

![enter image description here](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https://blog.kakaocdn.net/dn/oLHRl/btqIXgUevQB/RMWectPkhqPOOzzT9NMjKk/img.png)
- 트랜잭션이나 로깅, 보안과 같이 여러 모듈에서  **공통적으로 사용하는 기능의 경우 해당 기능을 분리**하여 관리할 수 있다.

### Spring Framework란 AOP (Aspect Oriented Programming) 관점 지향 프로그래밍이다.  

대부분은 객체 지향 프로그래밍을 지향하는 개발 프로세스인데,  중복된 코드들이 많아지고 가독성, 확장성, 유지보수성을 떨어뜨린다. AOP는 이 단점을 보완한다.  

Spring은 자체적으로 AOP를 지원하고 있기 때문에 트랜잭션이나 로깅, 보안과 같이 여러 비즈니스 모듈에서 공통적으로 필요로 하는 공통관심 사항을 핵심 로직과 분리시켜 각 모듈에 적용할 수 있음 

여러 오브젝트에 공통되는 코드를 모듈화하여 **무분별하게 중복되는 코드를 한 곳에 모아 중복 되는 코드를 제거 할 수 있어지고 공통기능을 한 곳에 보관함으로써 공통 기능 하나의 수정으로 모든 핵심기능들의 공통기능을 수정 할 수 있어 효율적인 유지보수가 가능하며 재활용성이 극대**화 될 수 있다. 

물론 AOP로 만들 수 있는 기능은 OOP로 구현 할 수 있는 기능이지만 Spring에서는 AOP를 편리하게 사용 할 수 있도록 이를 지원하고 있다. 

[추가적으로 AOP를 공부하려면 클릭](http://goddaehee.tistory.com/154)

##  5.영속성과 관련된 다양한 API 지원 및 연동 지원

- iBatis, myBatis나 Hibernate 등 완성도가 높은 데이터베이스처리 라이브러리와 연결할 수 있는 인터페이스를 제공한다.

##  6. 트랜잭션 관리 프레임워크

- 추상화된 트랜잭션 관리를 지원하며 설정파일(xml, java, property 등)을 이용한 선언적인 방식 및 프로그래밍을 통한 방식을 모두 지원한다.

##  7. 모델-뷰-컨트롤러 (MVC)  패턴

- 웹 프로그램밍 개발 시 거의 표준적인 방식인  **"Spring MVC"** 라 불리는 모델-뷰-컨트롤러(MVC) 패턴을 사용한다.

- DispatcherServlet이 Controller 역할을 담당하여 각종 요청을 적절한 서비스에 분산시켜주며 이를 각 서비스들이 처리를 하여 결과를 생성하고 그 결과는 다양한 형식의 View 서비스들로 화면에 표시될 수 있다. (추후에 Web에 들어가게 되면 이해가 될듯함) 

### Spring Framework의 MVC (Model2) 

![enter image description here](https://t1.daumcdn.net/cfile/tistory/9929B2345B9E4E002D)

 - MVC란 (Model View Controller) 구조로 사용자 인터페이스와 비지니스 로직을 분리하여 개발 하는 것 
  - MVC에서는 Model1과 Model2로 나누어져 있으며 일반적인 MVC는 Model2를 지칭
  
### MVC1
![enter image description here](https://i.imgur.com/rzhzcZc.png)

### MVC2
![enter image description here](https://i.imgur.com/keastvz.png)
MVC1과는 다르게 **Controller, View가 분리되어 있다.**

### Spring MVC Pattern 
![enter image description here](https://i.imgur.com/blr7x6q.png)

스프링에서는 유저의 요청을 받는 **DispathcerServlet**이 핵심이며 이것이 Front Controller의 역할을 맡는다. Front Controller(프런트 컨트롤러)란, 우선적으로 유저(클라이언트)의 모든 요청을 받고, 그 요청을 분석하여 세부 컨트롤러들에게 필요한 작업을 나눠주게 된다. 

**Model**

 - 데이터처리를 담당하는 부분
 - Serivce영역과 DAO영역으로 나누어지게 되고 여기서 중요한 것은 Service 부분은 불필요하게 HTTP통신을 하지 않아야하고 request나 response와 같은 객체를 매개변수로 받아선 안된다. 
 - 또한 Model 부분의 Service는 view에 종속적인 코드가 없어야 하고 View 부분이 변경되더라도 Service 부분은 그대로 재사용 할 수 있어야 한다.
 - **Model에서는 View와 Controller 어떠한 정보도 가지고 있어서는 안된다.**

**View**

- 사용자 Interface를 담당하며 사용자에게 보여지는 부분
-  View는 Controller를 통해 모델에 데이터에 대한 시각화를 담당하며 View는 자신이 요청을 보낼 Controller의 정보만 알고 있어야 하는 것이 핵심
- **Model이 가지고 있는 정보를 저장해서는 안되며 Model, Controller에 구성 요소를 알아서는 안됨**

**Controller**

- Controller에서는 View에 받은 요청을 가공하여 Model(Service 영역)에 이를 전달한다. 또한 Model로 부터 받은 결과를 View로 넘겨주는 역할을 한다. Controller에서는 모든 요청 에러와 모델 에러를 처리하며 View와 Controller에 정보를 알고 있어야한다.
- **Model과 View의 정보에 대해 알고 있어야한다.**

 이렇게 Model, View, Controller를 나누는 이유는 소스를 분리함으로서 각 소스의 목적이 명확해 지고 유지보수하는데 있어서 용이하기 때문이다. Model의 Service영역은 자신을 어떠한 Controller가 호출하든 상관없이 정해진 매개변수만 받는다면 자신의 비즈니스 로직을 처리할 수 있어야한다.

즉, 모듈화를 통해 어디서든 재사용이 가능하여야 한다는 뜻이다.

이말은 View의 정보가 달라지더라도 Controller에서 Service에 넘겨줄 매개변수 데이터 가공만 처리하면 되기 때문에 유지보수 비용을 절감 할 수 있는 효과가 있다. 또한 Service영역의 재사용이 용이하기 때문에 확장성 부분에서도 큰 효과를 볼 수 있는 장점이있다.

##  8. 배치 프레임워크

- 스프링은 특정 시간대에 실행하거나 대용량의 자료를 처리하는데 쓰이는 일괄 처리(Batch Processing)을 지원하는 배치 프레임워크를 제공한다. 기본적으로 스프링 배치는 Quartz 기반으로 동작한다.
- Quartz: 자바 스케줄링 오픈소즈 프레임워크 , **[Quartz](http://www.quartz-scheduler.org/)** is an open source job-scheduling framework written entirely in Java and designed for use in both _J2SE_ and _J2EE_ applications.
- https://www.baeldung.com/quartz

## 9. POJO

###  Spring Framework의 POJO란?

**POJO:** Plain Old Java Object 
![enter image description here](https://docs.spring.io/spring-framework/docs/4.3.30.RELEASE/spring-framework-reference/htmlsingle/images/container-magic.png)
**POJO란** 특정 규약 및 환경에 종속적이지 않은 평범한 일반 자바 클래스 의미 

**POJO의 조건**

1.  **특정규약에 종속되지 않는다.**
    
    POJO는 자바 언어와 꼭 필요한 API 외에는 종속되지 않아야 한다. EJB와 같이 특정 규약을 따라 비즈니스 컴포넌트를 만들어야 하는 경우는 POJO가 아니다. 특정 클래스를 상속해서 만들어야 하는 규약이 있는 경우도 마찬가지다.
    
2.  **특정 환경에 종속되지 않는다.**
    
    특정 환경에 종속적이어야만 동작하는 오브젝트도 POJO라고 할 수 없다. POJO는 환경에 독립적이어야 한다.

**POJO의 장점**

1.  특정기술과 환경에 종속되지 않은 오브젝트는 그만큼 깔끔한 코드가 될 수 있다.
    
2.  POJO로 개발된 코드는 자동화된 테스트에 매우 유리하다.
    
3.  **객체지향적인 설계를 자유롭게 적용할 수 있다.**


**Spring Framework 에서는  POJO을 지원한다.** 
- Spring 개발에 POJO 클래스를 활용할 수 있다는건 특정 구현 기술에 종속적이지 않다는 의미 
- 개발 후의 테스트시에도 DB와 특정 서버 없이도 테스트를 할 수 있기 때문에 개발이 빨라진다는 장점이 있음
- EJB와 다르게 기본 자바 클래스 코드 그대로 사용가능함 


## 10. 트랜잭션 처리를 위한 일관된 방법 제공

- 벤더사에 상관없이 처리를 일관된 방법을 사용하여 할 수 있게 한다. 
- JDBC API 및 JPA를 사용하거나 컨테이너가 제공하는 트랜잭션을 사용하든, 설정 파일을 통해 트랜잭션 관련 정보를 관리하기 때문에 특정 트랜잭션 구현 방법에 상관없이 동일 한 코드를 여러 환경에서 사용 가능

*즉 공통 부분의 소스 코딩이 용이하며 확장성도 매우 좋다*
  
[출처](https://goddaehee.tistory.com/156%5D%28https://goddaehee.tistory.com/156)


# 구조 

![enter image description here](https://t1.daumcdn.net/cfile/tistory/99A523405B9E2C1510)

## Spring Core

- Spring Container를 의미한다. 
- core라는 말 그대로 Container는 Spring Framework의 핵심이며 그중 핵심은 Bean Factory Container이다. 그 이유는 바로 Bean Factory는 IOC패턴을 적용하여 객체 구성 부터 의존성 처리까지 모든 일을 처리하는 역할을 하고 있기 때문이다.
- Spring 프레임워크의 근간이 되는요소. IoC(또는 DI) 기능을 지원하는 영역을 담당.
- BeanFactory를 기반으로 Bean 클래스들을 제어할 수 있는 기능을 지원
-   One main between  _BeanFactory_  and  _ApplicationContext_  is that  _BeanFactory_  only instantiates bean when we call  _getBean()_  method while  _ApplicationContext_  instantiates singleton bean when the container is started, It doesn't wait for  _getBean()_  method to be called.

![enter image description here](https://3.bp.blogspot.com/-l8GPByZH0LE/XEMvZ_p-XiI/AAAAAAAAFdQ/AmUVLRJDElAcrWjC8OjKD9P4QRimpcOzwCLcBGAs/s1600/beanfactory-vs-applicationcontext.jpg)


## Spring Context

- Spring context는 Spring Framework의 context 정보들을 제공하는 설정 파일이다. 
- Spring Context에는 JNDI, EJB, Validation, Scheduiling, Internaliztaion 등 엔터프라이즈 서비스들을 포함
- Spring Core 바로 위에 있으면서 Spring Core에서 지원하는 기능외에 추가적인 기능들과 좀 더 쉬운 개발이 가능하도록 지원
- 또한 JNDI, EJB등을 위한 Adaptor들을 포함


## Spring AOP

- Spring AOP module은 Spring Framework에서 관점지향 프로그래밍을 할 수 있고 AOP를 적용 할수 있게 도와주는 Module이다.
- Spring 프레임워크에 Aspect Oriented Programming을 지원하는 기능이다. 
  
## Spring DAO

- DAO란 Data Access Object의 약자로 Database Data에 접근하는 객체이다. 
- Spring JDBC DAO는 추상 레이어를 지원함으로써 코딩이나 예외처리 하는 부분을 간편화 시켜 일관된 방법으로 코드를 짤 수 있게 도와준다.
- 지금까지 우리들이 일반적으로 많이 사용해왔던 JDBC 기반하의 DAO개발을 좀 더 쉽고, 일관된 방법으로 개발하는 것이 가능하도록 지원
- Spring DAO를 이용할 경우 지금까지 개발하던 DAO보다 적은 코드와 쉬운 방법으로 DAO를 개발하는 것이 가능
  
 ### Code 예시
#### DAO 
```java
public  abstract  class AbstractJpaDAO< T extends Serializable > { 
		private Class< T > clazz; 
		@PersistenceContext 
		EntityManager entityManager; 

		public final void setClazz( Class< T > clazzToSet ){
		this.clazz = clazzToSet; } 

		public T findOne( long id ){ 
		return entityManager.find( clazz, id ); } 

		public List< T > findAll(){ 
		return entityManager.createQuery( "from " + clazz.getName() ) .getResultList(); } 

		public void create( T entity ){ 
		entityManager.persist( entity ); } 
		
		public T update( T entity ){
		return entityManager.merge( entity ); } 
	
		public void delete( T entity ){
		entityManager.remove( entity ); } 

		public void deleteById( long entityId ){
		T entity = findOne( entityId ); delete( entity ); } }
```
The persistence post processor is either created explicitly by defining it in the configuration or automatically, by defining  _context:annotation-config_  or  _context:component-scan_  in the namespace config.

Also, note that the entity  _**Class**_  is passed in the constructor to be used in the generic operations:
 ```java
 @Repository  
 public  class FooDAO extends AbstractJPADAO< Foo > implements IFooDAO{ 
 public FooDAO(){
  setClazz(Foo.class ); } }
```
  
## Spring ORM

- ORM이란 Object relational mapping의 약자로 간단하게 객체와의 관계 설정을 하는 것이다. Spring에서는 Ibatis, Hibernate, JDO 등 인기있는 객체 관계형 도구(OR도구)를 사용 할 수 있도록 지원합니다
 - Object Relation Mapping 프레임워크인 Hibernate, IBatis, JDO와의 결합을 지원하기 위한 기능
- Spring ORM을 이용할 경우 Hibernate, IBatis, JDO 프레임워크와 쉽게 통합하는 것이 가능

코드 예시: https://www.journaldev.com/7655/spring-orm-example-jpa-hibernate-transaction

## Spring Web

- Spirng에서 Web context module은 Application module에 내장되어 있고 Web기반의 응용프로그램에 대한 Context를 제공하여 일반적인 Web Application 개발에 필요한 기본적인 기능을 지원한다.  그로인해 Jakarta Structs 와의 통합을 지원한다.
  
## Spring MVC

- Spring에서는 MVC에서는 Model2 구조로 Aplication을 만들 수 있도록 지원한다. 
- MVC (Model-View-Controller) 프레임 워크는 웹 응용 프로그램을 작성하기위한 완전한 기능을 갖춘 MVC를 구현한다. 
- MVC 프레임 워크는 전략 인터페이스를 통해 고급 구성 가능하며 JSP, Velocity, Tiles, iText 및 POI를 포함한 수많은 뷰 기술을 지원하고 있다. 

 https://goddaehee.tistory.com/154?category=173020


# [Spring] Filter, Interceptor, AOP 차이 및 정리+

 https://goddaehee.tistory.com/154?category=173020

# Spring Annotation정리 
https://velog.io/@gillog/Spring-Annotation-%EC%A0%95%EB%A6%AC
