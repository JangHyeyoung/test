# test
# Spring 

# 목차
- [에러](#에러)
- [모르는 키워드](#모르는-키워드)
- [환경설정](#환경설정)
- [스프링 작성법](#스프링-작성법)
- [DI 개요 및 작성법](#DI-개요-및-작성법)
- [Annotation 개요 및 작성법](#Annotation-개요-및-작성법)
- [SpringMVC 개요 및 작성법](#SpringMVC-개요-및-작성법)
- [JNDI 개요 및 작성법](#JNDI-개요-및-작성법)
- [MyBatis DB 환경설정](#MyBatis-DB-환경설정)
- [Maven 사용법](#Maven-사용법)
- [Spring Tiles 개요 및 사용법](#Spring-Tiles-개요-및-사용법)
- [파일업로드](#파일업로드)

<br>

---

# 에러
## byType에러메세지
![5 byType에러메세지(하나의 타입에 해당하는 클래스만 존재)](https://user-images.githubusercontent.com/35926413/80326629-5dd44e00-8874-11ea-8d84-ef88fe3acb22.png)
하나의 타입에 해당하는 클래스만 존재

## `@Rquired` 에러메세지
![7 @Rquired에러메세지 확인](https://user-images.githubusercontent.com/35926413/80326724-abe95180-8874-11ea-811e-baea5869ccf8.png)
@Required 기능에 의해서 반드시 setNumber를 호출해야 되는데 호출하지 못해서 발생된 에러메세지

## 요청명령어
![12 요청명령어 에러발생메세지 출력](https://user-images.githubusercontent.com/35926413/80327554-772ac980-8877-11ea-9027-ab6f7e7263f3.png)
```
4월 14, 2020 12:26:04 오후 org.springframework.web.servlet.DispatcherServlet noHandlerFound
경고: No mapping found for HTTP request with URI [/SpringBoard/writeui.do]
 in DispatcherServlet with name 'board'
```
요청명령어가 등록이 되지 않아서 발생이 되는 에러메세지

## 객체 생성
![13 객체생성하지 않고 메서드호출하면 발생하는 에러메세지](https://user-images.githubusercontent.com/35926413/80327633-c40ea000-8877-11ea-865c-31cf5c03aefc.png)
객체 생성하지 않고 메서드 호출하면 발생하는 에러메세지

## Mybatis 에서 매개변수를 받을때 
![15 Mybatis의 주의할점](https://user-images.githubusercontent.com/35926413/80327705-fddfa680-8877-11ea-8e75-ed4506f51a21.png)
1. 값 입력
`#{매개변수}`는 멤버변수와 같아야 된다

2. 매개변수를 받는 위치가 중요
필드명, 특수기호가 포함되는 위치일 경우 `#{매개변수}` 를 `${매개변수}`로 써야된다.

## 다운로드 할 때의 뷰 객체
![22 다운로드할때 뷰객체생성안되면 지금과 에러가 발생](https://user-images.githubusercontent.com/35926413/80327975-c8878880-8878-11ea-848f-1d392cd8b866.png)
다운로드 할 때 뷰 객체가 생성안되면 위와같은 에러 발생

## 네임스페이스
```
nested exception is org.xml.sax.SAXParseException; 
lineNumber: 22; columnNumber: 57; 요소 유형 
"bean"과(와) 연관된 "p:number" 속성의 "p" 접두어가 바인드되지 않았습니다.
```
p네임스페이스를 이용한 값을 저장시키기 위해서는 xml위에 p네임스페이스
를 선언해야 된다.(선언하지 않아서 발생된 예외메세지)


<br>

[:arrow_up: TOP](#목차) 

<br>
<br>

# 모르는 키워드
## 네임 스페이스
#### p-네임스페이스
```xml
<bean id="" class="" p:속성명="값" p:멤버변수-ref="참조하는 구분자 id">

<bean id="moniter" class="spring4.SystemMoniter" 
p:periodTime="30" p:sender-ref="smsSender">
```

#### c-네임스페이스
```xml
<bean id="moniter" class="spring5.SystemMoniter" 
p:periodTime="30" p:sender-ref="smsSender2">
<!--  
  <constructor-arg value="30">
  <constructor-arg ref="smsSender2">
-->
</bean>
```

<br>

[:arrow_up: TOP](#목차) 

<br>
<br>

# 환경설정
## 이클립스에서 플러그인을 사용하는 방법
#### 1. plugin 설치
- plugin 다운받아 설치하는 방법은 가장 보편적인 방법
- 설치는 되나 가끔 실행되지 않는 버그
- plugin 주소도 수시로 변경되기 때문에 기존 url이 있다면 확인 후 설치
- `windows->perspective->open perspective->other` 설치된 plugin 등록
- 설치방법
  1. 경로 지정
  2. 설치 모듈 확인
  3. 동의 및 설치
  4. 경고 확인 및 이클립스 재부팅

#### 2. 웹상에서 STS을 검색해서 사용
- 대게는 STS(스프링)을 검색해 설치한다

<br>

[:arrow_up: TOP](#목차) 

<br>
<br>

# 스프링 작성법
## 스프링 프로젝트 생성
- Simple Java : 자바 app, Maven 사용 X
- Simple Spring Maven :자바 app, Maven 사용 O
- Simple Spring Web Maven : 스프링으로 웹프로그래밍
- Spring MVC Project : 완전한 자동화 툴, 초보자가 다루기는 어렵다

## 스프링의 특성
- **경량의 프레임워크**
- **MVC 프레임워크**를 제공(모델2 기반의 흐름)
- **DI**(Dependency Injection)를 지원(의존성 관계)
- **AOP**(Aspect Oriented Programming)를 지원한다(공통모듈 관리)
- **POJO**(Plain Old Java Objects)를 지원(웹상에서의 작업 지원)
- 트랜잭션 처리를 위한 일괄된 방법을 제공
- 영속성과 관련된 다양한 API를 제공
- 다양한 API에 대한 연동을 지원

## 스프링 사용 목적
- 큰 프로젝트의 프로그램의 수정
- 관련되는 모든 프로그램의 소스코드를 변경할 필요없다
- 유연성이 확보된다

## 빈즈객체
대규모 큰 프로젝트에서 사용하는 빈즈객체
```xml
<bean id="객체를 구분하는 인자번호" class="패키지명..클래스명"/>

<bean id="test"  class="spring.Message1" />
```

## 외부에서 라이브러리를 불러오는 방법
- 메이븐(Maven)은 pom.xml의 `<dependencies />`설정을 통해서 필요한 라이브러리를 다운받아서 저장소에 관리하는 역할을 한다. 
- `${버전변수명}`을 이용하면 일일이 바뀐버전명을 써주는것보다는 좀더 효율적으로 사용이 가능하다

```xml
<dependencies>
    <dependency>
        <groupId>상위패키지명.하위패키지명</groupId>
        <artifactId>jar파일의 이름</artifactId>
        <version>버전이름</version>
    </dependency>
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-context</artifactId>
        <version>${spring-framework.version}</version>
    </dependency>
<dependencies />
```


## 메이븐이란?
- 라이브러리 관리 프로그램
- 자동으로 라이브러리를 다운로드 받아서 처리해주는 툴

<br>

[:arrow_up: TOP](#목차) 

<br>
<br>

# DI 개요 및 작성법
## DI 개요
- 의존성 객체를 만들어서 원하는 위치에 넣어주는 기능
- has a 관계에 의해서 설정된 객체

## DI 종류
#### 1. 생성자를 이용한 DI
- constructor injection 방법
- 객체를 얻어와서 넣어준다 

#### 2. 멤버변수를 이용한 DI
- Setter injection 방법
- Setter Method를 이용해서 객체를 매개변수로 받아서 넣어주는 경우가 있다.

## 빈의 범위
#### singleton
생성된 하나의 객체를 요청할때마다 공유한다.
#### prototype
매번 요청할때마다 새로운 객체를 만들므로 메모리 낭비가 심할 수 있다.

## 클래스 간의 관계 설정
대체 뭐라고 써놓은 거야 ;;; 알아먹을 수가 없네
```xml
<constructor-arg  ref="주입할 객체id" />

<bean name="systemMoniter" class="spring10.SystemMoniter">
   <property name="call">
       <ref bean="phoneCall" /> <!-- 참조하는 상대방의 id -->
   </property>
</bean>

<bean id="phoneCall" class="spring10.PhoneCall" />
```

## DI와 DL
- DI : 의존객체를 넣어주는 관점
- DL : 의존객체를 어떻게 찾을 것인가의 관점

## byType, byName
#### byType
- 멤버변수의 자료형과 똑같은 자료형의 객체를 찾아서 넣어주는 기법
- 찾고자하는 자료형의 객체대상자가 한개이상이면 에러 발생
- 빈 객체의 속성에 `byType`을 설정
  ```xml
  <bean name="systemMoniter" class="spring10.SystemMoniter" 
    autowire="byType"></bean>
  ```
#### byName
멤버변수의 이름과 동일한 이름을 찾아서 객체를 넣어주는 기법
 ```xml
  <bean name="systemMoniter" class="spring10.SystemMoniter" 
    autowire="byName"></bean>
  ```

## 자신의 빈객체를 생성여부 옵션
해당 옵션을 사용할 경우 자바에서 객체를 생성하지 않기 때문에 추상 클래스가 된다.
- 생성하지 않을 때 : `abstract = true`
- 생성할 때 : `abstract = false`
```xml
<bean id="commonMoniter" class="spring11.SystemMoniter" abstract="true" >
   <property name="periodTime" value="10" />
   <property name="sender" ref="smsSender" />
</bean>
```

## 자식 빈즈에 상속 및 오버라이딩
`parent="부모빈즈의 id부여"` 상속이 되면서 오버라이딩까지 가능하다.
```xml
<bean id="commonMoniter" class="spring11.SystemMoniter" abstract="true" >
     <property name="periodTime" value="10" />
     <property name="sender" ref="smsSender" />
</bean>

<bean id="smsSender"  class="spring11.SmsSender" />

<!-- 1.부모의 멤버변수 그대로 사용(상속받으면 가능)-->
<bean id="doorMoniter" parent="commonMoniter" />

<!-- 2.상속을 받으면서 periodTime=30(오버라이딩) -->
<bean id="lobbyMoniter" parent="commonMoniter">
      <property name="periodTime" value="30" />
</bean>

<!-- 3.상속을 받으면서 periodTime=20(오버라이딩) -->
<bean id="roomMoniter" parent="commonMoniter">
      <property name="periodTime" value="20" />
</bean>
```

<br>

[:arrow_up: TOP](#목차) 

<br>
<br>

# Annotation 개요 및 작성법

## Annotation 작성법
- 찾고자하는 자료형의 객체대상자가 한개이상이면 에러가 발생

## Annotation 특징
- 환경설정부분을 단순하게 설정
- 자바코드의 일부 대용(어노테이션에도 기능이 있다)
- 어노테이션은 Spring 2.0, java 5 부터 제공

## Annotation 장점
- 시스템 복잡성이 아니라면 어노테이션 사용은 적합하게 쓰이면 코드가 간결해지고 유지보수가 용이해짐
- 대형 시스템엔 계층 구조가 잘 파악되기 위해서는 `web.xml` 사용이 필수
- 웹상에서 요청받아서 처리해주는 환경설정

## Annotation 단점
- 어노테이션은 메타정보가 소스코드에 들어가므로 파악하기 어려움
- 재 컴파일이 필요하다
- 소스코드가 같이 제공되지 않으면 사용에 제약이 따르기때문에 이해하기가 어렵다

## Annotation 종류
#### 1. 클래스명 위에 기술
#### `@Component`
- 패키지에 들어가 있는 모든 클래스를 자동적으로 빈즈객체로 등록을 시켜주는 어노테이션
- `@Component("등록하길 원하는 id값 부여")`
- @Component는 `@Named`로 대치 가능

#### 2. 멤버변수 위에 기술
#### 3. Setter 메서드, 일반 메서드 위에 기술
#### `@Required` 
- 메서드 위에 선언
- 반드시 호출해야 할 메서드임을 표시
- 반드시 호출해야되는데 호출하지 않은경우에 대비하기위해서 만들어진 어노테이션
#### `@Autowired`
- 멤버변수의 자료형과 똑같은 자료형의 객체를 찾아서 넣어주는 방법
- `@Inject`와 동일하다.
- 생성자,멤버변수,메서드에, Setter 메서드에 지정이 가능
- xml에 `<property>`태그 또는 `<p:멤버변수-ref="~">`생략해도 호출한다.
- 해당하는 빈즈객체가 없거나 두개이상 존재시 에러유발
- **디폴트 값 설정하는 방법**
  - `@Autowired(required=true)` : 찾은 빈즈가 있으면 넣어주고 없으면 에러유발
  - `@Autowired(required=false)` : 찾고자하는 빈즈가 없다면 찾아서 저장시켜달라
- **선언 위치별 특징**
  - 멤버변수 : Setter Method 호출없이 자동적으로 타입을 찾아서 저장
  - 메서드 : 메서드를 반드시 호출해서 해당되는 타입의 객체를 찾아서 저장
- 어노테이션과 관련된 클래스 import
  ```java
  import org.springframework.beans.factory.annotation.Autowired;
  ```
#### `@Resource`
속성에 지정된 객체를 Setter 메서드에 주입시켜준다
```xml
<bean id="camera5" class="anno4.Camera" />
```
```java
public class HomeController2 {
   private Camera camera;
   
    @Resource(name="camera5")
   public void setCamera(Camera camera) {
      this.camera = camera;
      System.out.println("setCamera() camera5이름을 가진 메서드 호출됨");
   }
}
```
#### `@PostConstruct`
객체가 생성전 @PostConstruct가 붙은 메서드를 먼저 호출시킨다
#### `@PreDestroy`
객체가 생성후 @PreDestroy가 붙은 메서드를 호출시킨다
#### `@RequestParam`
- `@RequestParam("전달받을 매개변수명")` 반환받는 변수자료형 받환받는 변수명
- `@RequestParam("num") String num` = `String num=request.getParameter("num")`   
  - 사용 : ${param.num}
- `@RequestParam(value="count(매개변수명)",defaultValue="20(디폴트값)")`
  request.getParameter("count")을 받는데 만약에 전달받은 값이 없다면 defaultValue="디폴트값(전달을 못받을시에 기본적으로 저장할값

#### `@Configuration`
환경설정을 xml대신에 자바파일로 설정할때 필요로하는 어노테이션
#### `@EnableWebMvc`
Spring MVC역할을 해주는 클래스라는것을 의미한다.
#### `@ComponentScan`
`@ComponentScan("spittr.web")` : spittr.web패키지에 들어가 있는 클래스를 빈즈로 등록
#### `@Bean`
XML 파일을 대신하는 순수 자바파일

<br>

## 스프링에서 빈즈객체 등록, 불러오는 방법
#### 1. xml파일을 가능한 안만들고 직접 자바의 클래스에 어노테이션을 이용해서 직접 빈즈를 만들고 등록하는 방법
xml파일이 없는 대신에 @Configuration,  @Bean 어노테이션을 이용사용

#### 2. 빈을 xml파일로 만들어서 환경설정을 하는 방법
spring 3.2 이전의 사용방법

#### 3. 어노테이션과 xml파일을 혼합해서 사용
가장 보편적인 방법

<br>

[:arrow_up: TOP](#목차) 

<br>
<br>

# SpringMVC 개요 및 작성법
## 작성법
모델2 -> 요청명령어 ->  commandPro.propreties에 등록 (/list.do=action.ListAction)

#### 1. 웹상에서 요청하는 컨트롤러의 이름 지정(요청 명령어 등록)
```xml
<servlet>
  <servlet-name>test</servlet-name> 
  <!-- test라는 별칭을 가진 서블릿을 찾음 -->
  <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class> 
  <!-- 컨트롤러 이름 -->
</servlet>      
```
#### 2. 웹상에서 요청할 때 어떻게 받아들일 것인가에 대한 설정
```xml
<servlet-mapping>
   <servlet-name>test</servlet-name> 
   <!-- test라는 별칭을 가진 서블릿을 찾아라 -->
   <!-- test-servlet.xml 을 생성 해줌-->
   <url-pattern>*.do</url-pattern> 
   <!--요청명령어가 ~.do로 요청이 들어왔을때 /를 거친 모든 요청명령어를 의미 -->
</servlet-mapping>
```
#### 3. `test-servlet.xml`에 설정
```xml
<bean name="요청명령어" class="org.springframework.web.servlet.mvc.ParameterizableViewController">
    <property name="viewName" value="이동할 페이지명"></property>   
</bean>
```
#### 4. 이동할 페이지의 확장자 지정
```xml
<bean id="viewResolver" class="org.springframework.web.servlet.view.InternalResourceViewResolver">
    <property name="viewClass" value="org.springframework.web.servlet.view.JstlView" />
    <property name="prefix" value="/" /> <!-- 페이지가 있는 상대경로를 지정 -->
    <property name="suffix" value=".jsp" /> <!-- 화면에 보여줄 페이지의 확장자 -->
</bean>
```

<br>

[:arrow_up: TOP](#목차) 

<br>
<br>

# JNDI 개요 및 작성법
JNDI(Java Naming Directory Interface)는 DB연결 정보로 Context.xml에 DBConnectionMgr.java(url,driver,계정,암호)를 저장하고 자동으로 연결한다

## 작성법
이게 맞는지도 모르겟다..
1.lib에 스프링 라이브러리 복사
2.web.xml에 스프링 컨트롤러 등록
```xml
<!-- 요청을 받아서 처리해주는 컨트롤러 등록(1)-->
  <servlet>
      <servlet-name>board</servlet-name>
      <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
  </servlet>
  
  <servlet-mapping>
      <servlet-name>board</servlet-name>
      <url-pattern>*.do</url-pattern>
  </servlet-mapping>
```
3.DB접속에 대한 테이블 생성및 DTO,DAO클래스 작성
4.board-servlet.xml파일생성(요청명령어 등록)
5.요청명령어에 해당하는 컨트롤러 클래스 작성(=액션클래스)
6.ListActionController 작성
- 사용자로부터 요청을 받아서 처리해주는 클래스(=액션클래스)
- handleRequest 메서드 이용하기 위해 Controller를 상속받아야 된다.
```java
public class ListActionController implements Controller {
    //...
}
```
7.list.jsp로 글목록보기 완성

<br>

[:arrow_up: TOP](#목차) 

<br>
<br>

# MyBatis DB 환경설정
- xml파일을 이용해서 SQL관리를 자바코드와 연결해서 관리해주는 프레임워크
- 프레임워크 : 스프링,MyBatis,SpringTiles

## MyBatis 장점
1. XML파일로 SQL문장을 관리하므로 가독성이 높아진다.
2. JDBC 드라이버가 있다면 어떤 DB에서도 사용이 가능하다.
3. DB연결 정보의 관리가 용이하다.
4. JavaBean 스타일의 클래스를 지원한다.
5. 여러 개의 DB에 접근이 쉽다.
6. Map,Collection,List와 기본형의 래퍼
7. 복잡한 객체 모델등을 쉽게 생성한다.

## MyBatis 단점
환경설정이 쉽지않다.

## 환경설정
1.Mybatis으로 변경
lib->Spring 3.x이상으로 설정->jar파일을 복사
2.DB연동
- WEB-INF/jdbc.properties파일 생성
- 생성된 파일은 web.xml에서 읽어들이기
3.DB환경설정 파일을 읽어들일 수 있도록 설정
```xml
<!-- 외부의 DB에 관련된 환경설정을 불러오는 경우(관련클래스,매개변수)-->
  <context-param>
     <param-name>contextConfigLocation(매개변수명)</param-name>
     <param-value>/WEB-INF/dataAccessContext-local.xml</param-value>
    <!-- (경로포함해서 불러올 파일명(상대경로) -->      
  </context-param>

<!--관련클래스  -->
  <listener>
      <listener-class>
         org.springframework.web.context.ContextLoaderListener
      </listener-class>
  </listener>
```

## POJO 개요
- Controller인터페이스나 AbstractCommandController추상클래스를 상속받아서 작성X
- 독립적으로 사용자로부터 요청을 받아서 처리해주는 기능을 가진 메소드를 직접 사용할 수가 있기때문에 상속받지않고 단독적으로 사용할 수 있는 클래스
- 컨트롤러역할을 하는 클래스가 되어야 한다(`@Controller`)

## POJO 특징
1. 인터페이스 or 추상클래스를 상속받지 않아도 된다.
2. `@Controller`를 부여
3. 자동적으로 컨트롤러 클래스가 된다.
4. 요청을 받아서 처리해주는 메서드를 개발자 마음대로 변경이 가능
5. 반환값은 보통 ModelAndView을 지정
6. 클래스 내부에 여러개의 메서드를 작성

<br>

[:arrow_up: TOP](#목차) 

<br>
<br>

# Maven 사용법

<br>

[:arrow_up: TOP](#목차) 

<br>
<br>

# Spring Tiles 개요 및 사용법
스프링에서 메인페이지를 만들어주는 프레임워크

## Spring web Maven을 선택한 경우(자동)
1.pom.xml->자바의 경우->버전 1.6->1.8로 변경
- `<java.version>1.8</java.version>` 
- 1.6->1.8로 변경
2.프로젝트 오 click->Build Configurer-> 1.6버전을 지우고->Add library JRE선택(1.8) 선택
3.Java Compiler 항목->1.6->1.8로 설정
4.Java Facets->Java ->1.8로 되어있는지를 확인
5.Runtimes ->Apache Tomcat v8.5 버전을 체크

## 수동으로 작업(처음부터 maven project 선택)
1.pom.xml->스프링에 관련된 jar
```xml
     <dependency>
        <groupId>org.apache.tiles</groupId>
        <artifactId>tiles-extras</artifactId>
        <version>3.0.1</version>
     </dependency>
     <dependency>
        <groupId>org.apache.tiles</groupId>
        <artifactId>tiles-servlet</artifactId>
        <version>3.0.1</version>
     </dependency>
     <dependency>
        <groupId>org.apache.tiles</groupId>
        <artifactId>tiles-jsp</artifactId>
        <version>3.0.1</version>
     </dependency>
```
2.컨트롤러 클래스를 작성->src/main/java가 폴더 존재X->수동으로 작업(폴더생성)
3.web.xml에서 DispatcherServlet을 등록->dispatcher 서블릿 별칭
 ->스프링에서 요청을 할때 맨 처음 실행(web.xml)
4.dispatcher-servlet.xml파일을 생성->요청명령어를 등록->작업

```
SpringTiles
     |
      -src=>컨트롤러 3개 작성
     |
       -WebContent(/)
                |
                 -WEB-INF
                       |
                        -lib(X)->maven project을 사용하지 않은경우->jar 복사해야한다
                       |
                        -tiles-def 폴더(1.타일즈에 대한 환경설정)
                               tilesdef.xml(화면에 어떻게 보일것인가에 대한 정보가
                                                 담겨져있는 tiles 환경설정 파일정보)
                       |
                        -tiles-view(2.메인페이지에서 보여줄 폴더 생성)
                                |
                                  -template->header.jsp(머리말)
                                                  menu.jsp(링크문자열)
                                                  **layout.jsp (본문 작성)**
                                                  footer.jsp(꼬리말)
                            body-menu1.jsp(링크를  걸어서 최종적으로 화면에 보여줄)
                            body-menu2.jsp
                            body.jsp
                      web.xml (1)
                      dispacter-servlet.xml(2)->타일즈 환경설정파일을 읽어들여라
```

## dispatcher-servlet.xml에서 tiles환경설정 파일을 불러오기
```xml
<!-- tiles에 관련된 환경설정을 불러오기(viewResolver가 조금 변환)
        기존의 prefix,suffix를 이용해서 경로명 및 파일의 확장자를 지정하는 부분X
   -->
<bean id="tilesConfigurer" class="org.springframework.web.servlet.view.tiles3.TilesConfigurer">
   <property name="definitions">
       <list>
          <value>/WEB-INF/tiles-def/tilesdef.xml</value>
       </list>
   </property>      
</bean>

<!-- viewResolver 설정 -->
<bean id="viewResolver" class="org.springframework.web.servlet.view.UrlBasedViewResolver">
    <property name="viewClass" 
     value="org.springframework.web.servlet.view.tiles3.TilesView"/>
</bean> 
```

## tiles-def.xml
- 메인 페이지를 불러올때 영역설정(top,left,body,footer) 이름 부여
- 영역에 맞는 불러올 파일명을 상대경로를 통해서 지정

## 한글처리
```xml
<filter>
  <filter-name>encodingFilter(필터의 별칭이름)</filter-name>
  <filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
  <!-- 패키지명...한글을 적용시킬 필터 클래스이름 -->
  <init-param>
      <param-name>encoding(필터클래스에 전달할 매개변수명)</param-name>
      <param-value>UTF-8(한글 캐릭터셋)(매개변수의 값)</param-value>
      <!--  UTF-8로 설정 -->
  </init-param>             
</filter>
    
<!-- 어떻게 요청시 한글이 지원이 되게 할것인가  -->
<filter-mapping>
    <filter-name>encodingFilter(적용시킬 필터별칭 이름)</filter-name>
    <url-pattern>/*(한글이 적용이 되는 대상자폴더를 지정)</url-pattern>
    <!-- Get방식으로 접속한 모든 요청경로 -->
</filter-mapping>
```
```xml
<filter>
    <filter-name>encodingFilter</filter-name>
    <filter-class>
       org.springframework.web.filter.CharacterEncodingFilter
    </filter-class>
    <init-param>
        <param-name>encoding</param-name>
        <param-value>UTF-8</param-value>
    </init-param>
</filter>
```

<br>

[:arrow_up: TOP](#목차) 

<br>
<br>

# 파일업로드

<br>

[:arrow_up: TOP](#목차) 

<br>
<br>
