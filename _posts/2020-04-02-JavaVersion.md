---
layout : single
title : "Java Version"
date : 2020-04-02
categories : JAVA
---

# JAVA버전에 따른 기능의 차이점

201701691 이상민



## 1. JDK 1.0a2

- 출시 : 1995.05.23

- 정식 발표된 최초의 Java언어.



## 2. JDK 1.0

- 출시 : 1996.01.23
- Oak라는 이름에서 JAVA라는 이름으로 명칭 변경됨.



## 3. JDK 1.1

- 출시 : 1997.02.19
- 이너 클래스, JavaBeans, RMI, 리플렉션, 유니코드 지원, 국제화 등 추가



## 4. J2SE 1.2

- 출시 : 1998.12.08 (지원 종료 : 2003.11)
- 새로운 GUI, JIT, CORBA 등 기능 추가.
- Strictfp, Swing GUI, JIT, Java Applet을 구동하는 웹 브라우저 플러그인, CORBA, Collection 등 추가
- 1999년 업데이트를 통해 HotSpot JVM이 첫 선을 보임.



## 5. J2SE 1.3

- 출시 : 2000.03.08 (지원 종료 : 2006.11)
- Hotspot JVM, JNDI, JPDA, JavaSound 등 추가
- RMI가 CORBA를 지원하도록 변경



## 6. J2SE 1.4

- 출시 : 2002.02.06 (지원 종료 :  2013.02)
- Assert, 정규표현식, IPv6, Non-Blocking IO, XML API, JCE, JSSE, JAAS, Java Web Start 등이 추가



## 7. J2SE 5

- 출시 : 2004.09.30 (지원 종료 : 2015.05)
- Generics, Annotation, Auto Boxing/Unboxing, Enumeration, 가변 길이 파라미터, Static Import, 새로운 Concurrency API 등이 추가
- 기존 자바는 표준 입력(stdin)이 부족했으나 이 버전부터 java.util.Scanner가 추가되면서 이전보다 편하게 표준 입력 사용이 가능해짐.



## 8. Java SE 6

- 출시 : 2006.12.11 (지원 종료 : 2018.12)
- Scripting Language Support, JDBC 4.0, Java Compiler API, Pluggable Annotation 등이 추가됨.
- 스크립팅 언어 지원과 함께 Rhino JavaScript 엔진이 기본 탑재



## 9. Java SE 7

* 출시 : 2011.07.07 (지원 종료 예정 : 2022.07)
* Dynamic Language 지원, Swtich문에서 String 사용
* try문에서 자동 자원 관리, Diamond Operatior <> 추가
* 이진수 리터럴, 숫자 리터럴에 _ 지원, 새로운 Concurrency API 추가
* 새로운 File NIO 라이브러리, Elliptic Curve Cryptography, Java2D를 위한 XRender, Upstream, Java Deployment Ruleset 등이 추가



## 10. Java SE 8

* 출시 : 2014.03.18 (지원 종료 예정 : 2023.09)
* Lambda Expression 추가, Rhino 대신 Nashorn Java Script 엔진 탑재
* Annotation on Java Types 추가, Unsigned Integer 계산
* Repeating Annotation, 새로운 날짜와 시간 API(JodaTime) 추가
* Static Link JNI Library, Interface Default Method, Stream API 추가
* PermGen 영역 삭제
* 32비트를 지원하는 마지막 공식 Java 버전. 이후 버전의 32비트 지원은 오직 서드파티를 통해서만 지원함.



## 11. Java SE 9

- 출시 : 2017.09.21
- Project Jigsaw 기반으로 런타임이 모듈화됨으로서 AWT나 Swing같은 불필요한 라이브러리를 끌어쓸 필요 없이, 최상위 모듈인 Base만 사용해도 됨. 
- 특정 프로그램에 최적화된 최소 런타임을 제작할 수 있게 되면서 패키징이 간편해짐.
- JShell이 추가되었고 Java 바이트코드를 기계어로 미리 번역하는 선행 컴파일(Ahead-Of-Time Compilation) 역시 실험 기능으로 추가됨.
- Deprecated 표시에는 해당 버전과 제거 예정 여부를 표시할 수 있게 됨.
- 구조적 불변 컬렉션, 통합 로깅, HTTP/2, private 인터페이스 메소드, HTML5 Javadoc 등 지원
- 프로퍼티 파일에 UTF-8이 지원됨에 따라 인코딩 문제 해결
- Java Applet 기능 지원 종료됨.
- 이 버전부터 64비트 버전만 출시되며 32비트 버전은 공식적으로 나오지 않음.



## 12. Java SE 10

* 출시 : 2018.03.20
* var 키워드를 이용한 지역 변수 타입 추론, 병렬 처리 가비지 컬렉션, 개별 쓰레드로 분리된 Stop-The-World, 루트 CA 목록 등이 추가.
* JDK의 레포지토리가 하나로 통합됨.
* JVM 힙 영역을 시스템 메모리가 아닌 다른 종류의 메모리에도 할당할 수 있게 됨.
* 실험 기능으로 Java 기반의 JIT 컴파일러가 추가되었고 이전 버전에서 Deprecated 처리된 API는 이 버전에서 모두 삭제됨.



## 13. Java SE 11

* 출시 : 2018.09.25
* 이클립스 재단으로 넘어간 Java EE가 JDK에서 삭제되고, JavaFX도 JDK에서 분리되어 별도의 모듈로 제공됨.
* 람다 파라미터에 대한 지역 변수 문법, 엡실론 가비지 컬렉터, HTTP 클라이언트 표준화 등의 기능 추가.



## 14. Java SE 12

* 출시 : 2019.03.19
* 가장 큰 특징은 문법적으로 Swtich 문을 확장함.

```java
switch (day) {
    case MONDAY:
    case FRIDAY:
    case SUNDAY:
        System.out.println(6);
        break;
    case TUESDAY:
        System.out.println(7);
        break;
    case THURSDAY:
    case SATURDAY:
        System.out.println(8);
        break;
    case WEDNESDAY:
        System.out.println(9);
        break;
}
```

-이전 버전에서의 Swtich 문 사용-

```java
switch (day) {
    case MONDAY, FRIDAY, SUNDAY -> System.out.println(6);
    case TUESDAY                -> System.out.println(7);
    case THURSDAY, SATURDAY     -> System.out.println(8);
    case WEDNESDAY              -> System.out.println(9);
}
```

-Java SE 12부터의 Swtich 문 사용-

* 이 외에 가비지 컬렉터 개선, 마이크로 벤치마크 툴 추가, 성 능 개선 등 변경점이 있음.



## 15. Java SE 13

* 출시 : 2019.09.17
* yield라는 예약어가 추가됨.

```java
var a = switch (day) {
        case MONDAY, FRIDAY, SUNDAY -> yield 6;
        case TUESDAY                -> yield 7;
        case THURSDAY, SATURDAY     -> yield 8;
        case WEDNESDAY              -> yield 9;
};
```



