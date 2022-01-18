# 인프런 스프링 핵심 원리 기본편

## 스프링이란 ?
### 핵심기술
스프링 DI 컨테이너, AOP, 이벤트, 기타

### 스프링 부트
스프링을 편리하게 사용할 수 있도록 지원, 최근에는 기본으로 사용

### 스프링 단어 ?
스프링 DI 컨테이너 기술  
스프링 프레임워크  
스프링 생태계

### 핵심 개념
자바 언어 기반의 프레임워크  
객체 지향 언어  
객체 지향 언어의 특징을 살려내는 프레임워크  
좋은 객체 지향 애플리케이션을 개발할 수 있게 도와주는 프레임워크

## 좋은 객체 지향 프로그래밍
### 객체 지향 프로그래밍
객체들의 모임으로 파악하고자 하는 것  
각 객체는 메시지를 주고받고 데이터를 처리할 수 있다 ( 협력 )  
프로그램을 유연하고 변경이 용이하게 만들어준다

### 유연하고, 변경이 용이
컴포넌트를 쉽고 유연하게 변경하면서 개발할 수 있는 방법

### 다형성
#### 역할과 구현을 분리
예) 운전자( 클라이언트 ) -> 차 ( 역할 ) -> 차종 ( 구현 ) 의 개념  
장점  
대상의 역할만 알면 된다  
내부 구조를 몰라도 된다  
내부 구조가 변경되어도 영향을 받지 않는다.  
대상 자체를 변경해도 영향을 받지 않는다.  

단점  
역할 ( 인터페이스 ) 자체가 변하면, 클라이언트, 서버 모두에 큰 변경 발생  
인터페이스를 안정적으로 잘 설계하는 것이 중요하다

#### 다형성의 본질
인터페이스( 역할 )를 구현한 객체 인스턴스( 리파지토리, 구현체 ) 를 실행 시점에 유연하게 변경할 수 있다  
본질을 이해하려면 협력이라는 객체사이의 관계에서 시작해야한다  
클라이언트를 변경하지 않고, 서버의 구현 기능을 유연하게 변경할 수 있다

### 스프링과 객체 지향
다형성을 극대화해서 이용할 수 있게 도와준다  
제어의 역전(Ioc), 의존관계 주입(DI)은 다형성을 활용해서 역할과 구현을 편리하게 다룰 수 있도록 지원한다  
스프링은 차종을 선택하듯이 구현을 편리하게 변경할 수 있다

## 좋은 객체 지향 설계의 5가지 원칙 (SOLID) !!!!! 면접 질문 가능성 있음 !!!!!
SRP: 단일 책임 원칙  
OCP: 개방-폐쇄 원칙  
LSP: 리스코프 치완 원칙  
ISP: 인터페이스 분리 원칙  
DIP: 의존관계 역전 원칙

### SRP 단일 책임 원칙
한 클래스는 하나의 책임만 가져야 한다  
중요한 기준은 변경이 있을 때 파급 효과가 적게 만드는 것  
예) UI 변경, 객체의 생성과 사용을 분리

### OCP 개방-폐쇄 원칙 !!중요!!
확장에는 열려 있으나 변경에는 닫혀 있어야 한다  
다형성을 활용  
인터페이스를 구현한 새로운 클래스를 하나 만들어서 ( 리파지토리? ) 새로운 기능을 구현  

### LSP 리스코프 치환 원칙
예) 자동차 인터페이스 엑셀 = 전진 / 후진하게 구현하면 위반  
프로그램의 정확성을 깨뜨리지 않으면서 하위 타입의 인스턴스로 바꿀 수 있어야 한다  
다형성에서 하위 클래스는 인터페이스 규약을 다 지켜야 한다는 것  
다형성을 지원하기 위한 원칙  
인터페이스를 구현한 구현체는 믿고 사용하려면, 이 원칙이 필요하다  
단순히 컴파일에 성공하는 것을 넘어서는 이야기

### ISP 인터페이스 분리 원칙
특정 클라이언트를 위한 인터페이스로 분리  
인터페이스가 명확해지고 대체 가능성이 높아진다

### DIP 의존관계 역전 원칙 !!중요!!
구현체의 의존하지 말고 역할 ( 인터페이스 ) 에 의존한다


## 객체 지향 설계와 스프링
### 스프링 이야기에 왜 객체 지향 이야기가 나오는가?
DI ( 의존관계, 의존성 주입 ), DI 컨테이너 기술로 다형성 + OCP, DIP를 가능하게 지원  
클라이언트 코드의 변경 없이 기능 확장 ( 부품 교체 개발 )

## 스프링 핵심 원리 이해
### Config ( DI 컨테이너 )
구현체에 의존을 대신 주입 해줌으로써 DIP 원칙을 지킬 수 있다

### IoC 제어의 역전
제어 흐름을 외부에서 관리하는 것을 의미한다

### 프레임워크 vs 라이브러리
내가 작성한 코드를 제어하고, 대신 실행하면 프레임워크 ( JUnit )  
내가 작성한 코드가 직접 제어의 흐름을 담당하면 라이브러리

### 의존관계 주입 DI
정적인 클래스 의존 관계와, 실행 시점에 결정되는 동적인 객체(인스턴스) 의존 관계를 분리해서 생각해야 한다

#### 정적인 클래스 의존관계
import 코드만 보고 의존관계를 쉽게 판단할 수 있다  
애플리케이션을 실행하지 않아도 분석할 수 있다

#### 동적인 객체 인스턴스 의존 관계
애플리케이션 실행 시점에 실제 생성된 객체 인스턴스의 참조가 연결된 의존관계다

#### 의존관계 주입
실행 시점( 런타임 )에 외부에서 구현 객체를 생성하고 클라이언트에 전달해서 클라이언트와 서버의 외존관계가 연결 되는 것  
장점  
클라이언트 코드를 변경하지 않고, 클라이언트가 호출하는 대상의 타입 인스턴스를 변경할 수 있다  
정적인 클래스 의존관계를 변경하지 않고, 동적인 객체 인스턴스 의존관계를 쉽게 변경할 수 있다

### IoC 컨테이너, DI 컨테이너
Config 처럼 객체를 생성하고 관리하면서 의존관계를 연결해 주는 것  
의존관계 주입에 초점을 맞춰 최근에는 주로 DI 컨테이너라 한다

## 스프링 컨테이너와 스프링 빈
### 스프링 컨테이너
ApplicationContext 를 스프링 컨테이너라 한다  
@Bean 이 붙은 메서드의 명을 스프링 빈의 이름으로 사용한다

### 스프링 컨테이너 생성
@Bean 이 붙은 메서드들을 스프링 컨테이너에 등록한다 (메서드 이름 (@Bean(name = "이름") 방식으로 지정 가능): 키, return : 객체)

### BeanFactory와 ApplicationContext
ApplicationContext가 BeanFactory를 상속받는다  
일반적으로 ApplicationContext만 사용한다

#### ApplicationContext가 제공하는 부가기능
메시지소스를 활용한 국제화 기능 예) 한국 -> 한국어  
환경변수 : 로컬, 개발, 운영등을 구분해서 처리  
애플리케이션 이벤트 : 이벤트를 발행하고 구독하는 모델을 편리하게 지원  
편리한 리소스 조회 : 파일, 클래스패스, 외부 등에서 리소스를 편리하게 조회

## 싱글톤 컨테이너
### 스프링 없는 순수한 DI 컨테이너
요청을 할 때 마다 객체를 새로 생성한다. ( 메모리 낭비가 심하다 )

### 싱글톤 패턴
클래스의 인스턴스가 딱 1개만 생성되는 것을 보장한다  
static 영역에 객체를 미리 생성하고 특정 메서드를 통해서만 조회가 가능하도록 만든다    
생성자를 private으로 막아서 외부 생성이 불가능 하도록 한다    

문제점  
구현 코드가 많이 들어간다.  
구체 클래스에 의존한다 -> DIP 위반, OCP 위반 가능성이 높다  
테스트하기 어렵다

### 싱글톤 컨테이너
이미 만들어진 객체를 공유해서 효율적으로 재사용할 수 있다

### 싱글톤 방식의 주의점
무상태(stateless)로 설계해야 한다 -> 공유필드를 수정하지 못하도록 해야한다

### @Configuration
@Bean이 붙은 메서드마다 이미 스프링 빈이 존재하면 존재하는 빈을 반환하고,   
스프링 빈이 없으면 생성해서 스프링 빈으로 등록하고 반환하는 코드가 동적으로 만들어진다  
이를 통해 싱글톤 패턴이 지켜진다

## 컴포넌트 스캔
### @ComponentScan
@Component 어노테이션이 붙어있는 클래스들을 스프링 빈으로 등록한다  
#### basePackages
탐색 패키지 시작 위치를 정한다  
지정하지 않으면 @ComponentScan 이 붙은 설정 정보 클래스의 패키지가 시작 위치가 된다
### @Autowired
생성자에서 의존관계 자동 주입

## 의존관계 자동 주입
### 생성자 주입
생성자 호출시점에 딱 1번만 호출되는 것이 보장된다  
불변, 필수 의존관계에 사용

### 수정자 주입(setter 주입)
선택, 변경 의존관계에 사용

### 필드 주입
외부에서 변경이 불가능해서 테스트 하기 힘들다는 치명적인 단점이 있다  
테스트코드 정도를 제외하고는 사용하지 말자

### 메서드 주입
한번에 여러 필드를 주입 받을 수 있다  
일반적으로 잘 사용하지 않는다

### 옵션 처리
@Autowired(required=false) : 자동 주입할 대상이 없으면 수정자 메서드 자체가 호출 안됨  
org.springframework.lang.@Nullable : 자동 주입할 대상이 없으면 null이 입력된다  
Optional<> : 자동 주입할 대상이 없으면 Optional.empty 가 입력된다

### 생성자 주입을 선택해라!
대부분의 의존관계 주입은 한번 일어나면 애플리케이션 종료시점까지 의존관계를 변경할 일이 없다.  
오히려 대부분의 의존관계는 애플리케이션 종료 전까지 변하면 안된다

### 롬복과 최신 트랜드
@RequiredArgsConstructor : final이 붙은 인터페이스( 역할 객체 ) 자동 생성자 생성

### 조회 빈이 2개 이상일 경우 해결방법
@Autowired : 파라미터 이름을 구현 클래스 이름으로 해준다  
@Qualifier : 추가 구분자를 만들어준다  
★ @Primary : 우선권을 부여한다

### 조회할 빈이 2개 이상 필요할 경우
Map<String, 타입>  
map의 키에 스프링 빈의 이름을 넣어주고, 해당 타입으로 조회한 모든 스프링 빈을 담아준다  
List<타입>  
타입으로 조회한 모든 스프링 빈을 담아준다  
공통  
해당 타입의 빈이 없으면 빈 컬랙션이나 Map을 주입

### 수동 빈 등록을 해야하는 경우
광범위하게 영향을 미치는 기술 지원 객체  
다형성을 적극 활용하는 비즈니스 로직 ( 읽기 좋은 코드를 위해 )

