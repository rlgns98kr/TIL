#  Spring

## 계획

### Framework

- DI, Spring-Test, jdbc, MyBatis, AOP, Servlet/JSP, Spring MVC (JSP,k JSTL)
- Rest Service (JSON, XML)

### Boot

- JPA, Spring MVC(Thymeleaf), REST
- Spring Security



## 기본

- override -> 상속관계에서 자식이 부모의 method와 같은 method를 선언하였을 때 자식의 method로 override
- 추상 method는 body를 가질 수 없다. 따라서 모두 override 시켜야 한다.
- interface 는 추상클래스이므로 선언된 method는 모두 override 시켜야 한다.

- package 작명규칙 ex) kbstar.cms(업무이름).dao(data access object, db연결) .service(biz logic) .controller(front end와 back end 연결) .vo(value object)/entity/dto(data transfer object)/javabeans .exception(사용자 정의) .mapper

  \* 패키지 명은 소문자를 쓰는게 좋다.

- 추상클래스는 추상메서드를 반드시 하나 가지지 않아도 되나 객체를 생성할 수는 없다.
- 부모의 type으로 객체를 생성하였을 때 부모가 주는 method만 실행가능하다. method가 추상일 경우에는 생성자(자식) 클래스의 method를 사용
- 다형적 인자에는 자식 클래스들이 들어갈 수 있다.
- static 메서드에서는 nonstatic method를 바로 호출할 수 없다.(메모리 공간(주소)가 다름)



### 단축키

- ctrl + s : save
- ctrl + shift + o : auto import
- ctrl + space : auto code complete



## 개요

### 프레임워크

- 비기능적인 요소들을 어느정도 제공해준다.
- 기능적인 요구사항에 집중가능
- 디자인 패턴과 마찬가지로 반복적으로 발견되는 문제들을 해결하기 위한 solution을 제공

\* WAS : Web Container + EJB Container, J2EE API 구현체, 미들웨어



### 프레임워크/라이브러리

- 통제(메서드의 실행)의 권한이 개발자에게 있는가?
  - 있음 -> 라이브러리
  - 없음 -> 프레임워크
- 프레임워크는 개발자의 코드를 호출하기 때문에 개발자가 제어할 수 없다.

