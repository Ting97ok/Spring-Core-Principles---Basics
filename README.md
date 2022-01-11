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
