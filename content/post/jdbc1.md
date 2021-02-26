---
title: "JDBC 환경세팅"
date: 2020-09-15T11:30:03+00:00
weight: 1
aliases: ["/jdbc2"]
tags: ["JDBC"]
categories: ["JDBC"]
series: ["JDBC"]
author: "Me"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
disableShare: false
comments: false
---

## JDBC 환경세팅

### CASE: 하나의 Team에는 한명의 Member가 있는 상황 @OneToOne

1. eclipse에서 new java project 생성 
2. 마우스 오른쪽 클릭 → configure → maven project 
3. 마우스 오른쪽 클릭 → configure → JPA project 
4. pom.xml setup
    - Dependency & Repository setup 

        ```
        <dependencies>
                <dependency>
                    <groupId>javax.persistence</groupId>
                    <artifactId>javax.persistence-api</artifactId>
                    <version>2.2</version>
                </dependency>
                <dependency>
                    <groupId>org.hibernate</groupId>
                    <artifactId>hibernate-entitymanager</artifactId>
                    <version>5.4.2.Final</version>
                </dependency>

                <dependency>
                    <groupId>org.projectlombok</groupId>
                    <artifactId>lombok</artifactId>
                    <version>1.18.8</version>
                </dependency>
                <dependency>
                    <groupId>com.jslsolucoes</groupId>
                    <artifactId>ojdbc6</artifactId>
                    <version>11.2.0.1.0</version>
                </dependency>

                <dependency>
                    <groupId>org.junit.platform</groupId>
                    <artifactId>junit-platform-runner</artifactId>
                    <version>1.0.1</version>
                    <scope>test</scope>
                </dependency>

                <dependency>
                    <groupId>org.junit.jupiter</groupId>
                    <artifactId>junit-jupiter-engine</artifactId>
                    <version>5.0.1</version>
                </dependency>

                <dependency>
                    <groupId>org.junit.jupiter</groupId>
                    <artifactId>junit-jupiter-params</artifactId>
                    <version>5.0.1</version>
                    <scope>test</scope>
                </dependency>

                <!-- @Slf4j 사용을 위한 library 설정 & log4j.properties 필요 -->
                <dependency>
                    <groupId>org.slf4j</groupId>
                    <artifactId>slf4j-api</artifactId>
                    <version>1.7.5</version>
                </dependency>
                <dependency>
                    <groupId>org.slf4j</groupId>
                    <artifactId>slf4j-log4j12</artifactId>
                    <version>1.7.5</version>
                </dependency>
            </dependencies>

            <repositories>
                <repository>
                    <id>oracle</id>
                    <name>ORACLE JDBC Repository</name>
                    <url>https://maven.atlassian.com/3rdparty/</url>
                </repository>
            </repositories>
        ```

5. log4j properties 파일을 src 안으로 복사하고 붙여넣는다.  
    - log4j.properties

        ```
        # Set root category priority to INFO and its only appender to CONSOLE.
        log4j.rootCategory= INFO, CONSOLE, daily 
        \u200B
        # CONSOLE is set to be a ConsoleAppender using a PatternLayout.
        log4j.appender.CONSOLE=org.apache.log4j.ConsoleAppender
        log4j.appender.CONSOLE.layout=org.apache.log4j.PatternLayout
        log4j.appender.CONSOLE.layout.ConversionPattern=- [%-p] %m%n
        \u200B
        log4j.appender.daily=org.apache.log4j.DailyRollingFileAppender
        log4j.appender.daily.File=C:\\ITStudy\\88.log\\fiveguys.log
        #C:\\ITStudy\\88.log
        log4j.appender.daily.DatePattern='.'yyyy-MM-dd
        log4j.appender.daily.layout=org.apache.log4j.PatternLayout
        log4j.appender.daily.layout.ConversionPattern=- [%-p] %d{dd-MM-yyyy HH:mm:ss} %F %m%n
        ```

6. META INF 안의 persistence.xml 파일 설정
    - persistence.xml

        ```
        <?xml version="1.0" encoding="UTF-8"?>
        <persistence version="2.1" xmlns="http://xmlns.jcp.org/xml/ns/persistence" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/persistence http://xmlns.jcp.org/xml/ns/persistence/persistence_2_1.xsd">
            <persistence-unit name="oracleDBUse">
                <class>entity2.Member</class>
                <class>entity2.Team</class>
        <!--        <class>entity.Member</class>
                <class>entity.Team</class> -->
            <!-- <class>step01.entity.Dept01</class> -->    
                <properties>
                    <property name="javax.persistence.jdbc.driver" value="oracle.jdbc.OracleDriver" />
                    <property name="javax.persistence.jdbc.url" value="jdbc:oracle:thin:@127.0.0.1:1521:xe" />
                    <property name="javax.persistence.jdbc.user" value="SCOTT" />
                    <property name="javax.persistence.jdbc.password" value="TIGER" />

                    <property name="hibernate.dialect" value="org.hibernate.dialect.OracleDialect" />

                    
                    <property name="hibernate.show_sql" value="true" />
                    <property name="hibernate.format_sql" value="true" />
                    <!--<property name="hibernate.use_sql_comments" value="true" /> -->
                    <property name="hibernate.id.new_generator_mappings" value="true" />

                    
                    <property name="hibernate.hbm2ddl.auto" value="create" />  
                    <!-- <property name="hibernate.hbm2ddl.auto" value="none" />  -->
                    
                    </properties>
            </persistence-unit>
        </persistence>
        ```

        persistence.xml 파일에서 db 접속 정보 설정 tag 확인해서 아이디 패스워드 확인 

7. Entity, Test 와 Util java class를 만들어서 테스트 환경 조성 
    - Entity
        주의사항 

        1. @Entity 애노테이션선언
        2. persistence.xml 에 등록 (persistence file 눌러 JPA synchronize 하여 class 연동하기)
        3. 각 컬럼별 이름, 사이즈 조절
        4. String 타입은 length로 사이즈 조절
        5. Number 타입읁 BigDecimal, precision으로 조절
        6. @Column
        7. @GeneratedValue(strategy=GenerationType.SEQUENCE


            ```
            //콘솔창에 뜨는 해당 사항 
            drop sequence hibernate_sequence
            Hibernate: create sequence hibernate_sequence start with 1 increment by 1
            3.@Column(length=20, nullable=false)
            ```

        - Team (Parent Class)

            ```java
            @NoArgsConstructor
            @AllArgsConstructor

            @Builder
            @Getter
            @Setter

            @Entity
            @SequenceGenerator(name="TEAM_ID_SEQ",
                               sequenceName = "TEAM_SEQ",
                               initialValue = 1,
                               allocationSize = 50)

            public class Team {
                @Id
                @GeneratedValue (strategy=GenerationType.SEQUENCE,
                generator="TEAM_ID_SEQ") 
                @Column (name="team_id")
                private Long teamId;
                
                @Column (name = "team_name", length  = 20)
                private String teamName; 
            }
            ```

        - Member (Child Class)

            ```java
            @NoArgsConstructor
            @AllArgsConstructor

            @Builder
            @Getter
            @Setter

            @Entity
            @SequenceGenerator(name="MEMBER_ID_SEQ",
                               sequenceName = "MEMBER_ID",
                               initialValue = 1,
                               allocationSize = 50)

            public class Member {
                @Id
                @GeneratedValue (strategy=GenerationType.SEQUENCE,
                        generator="MEMBER_ID_SEQ") //sequence
                
                @Column (name="member_id")
                private Long memberId;
                
                @Column (name = "member_name", length  = 20)
                private String memberName; 
                
                @Column (name="member_age")
                private Integer memberAge;
                
                @OneToOne
                @JoinColumn (name = "team_id", referencedColumnName = "team_id") 
                private Team teamId; 
            }
            ```

    - Test

        EntityManager의 개별 메소드로 crud 하는 실행 클래스 

        ```java
        public class RunningTest {
            //step02
            @Test
            public void runningTest() {
                EntityManager em = PublicCommon.getEntityManager();

                EntityTransaction tx = em.getTransaction();
                tx.begin();

                try {
                    Team t1 = Team.builder().teamName("team A").build();
                    em.persist(t1);
                    Team t2 = Team.builder().teamName("team B").build();
                    em.persist(t2);
                    
                    // member 객체 생성 후 insert 시도할 경우 member의 teamid는 이미 존재하는 team 이어야함
                    Member m1 = Member.builder().memberName("유재석").teamId(t1).memberAge(50).build();
                    em.persist(m1);
                    Member m2 = Member.builder().memberName("강재석").teamId(t2).memberAge(40).build();
                    em.persist(m2);
                    
                    tx.commit();
                } catch(Exception e) {
                    e.printStackTrace();
                } finally {
                    em.close();
                }
            }
        ```

    - Util

        실행 클래스에 활용될 Util 클래스 개발 

        1. EntiyManagerFactory
        2. EntityManager

        ```java
        package util;

        import javax.persistence.EntityManager;
        import javax.persistence.EntityManagerFactory;
        import javax.persistence.Persistence;

        public class PublicCommon {
            //db driver처럼 한번만 메모리 생성 후 저장 및 쭉 재사용 
            private static EntityManagerFactory emf; //멤버변수 초기화
            static { 
                 emf = Persistence.createEntityManagerFactory("oracleDBUse");
            }
            
            //CRUD 로직별 생성 및 client는 공유 금지 
            //EntityManager 반환 
            public static EntityManager getEntityManager() {
                return emf.createEntityManager();
            }
            
            //자원반환  em.close()는 매번 상황에 맡겨서 하기 
            public static void close(EntityManager em) {
                emf.close();
            }
        }
        ```
