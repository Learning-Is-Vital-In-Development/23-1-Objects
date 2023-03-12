
## ****7장 기능 분해****

---

사람의 기억은 **단기 기억** 과 **장기 기억**으로 분류할 수 있다.

**단기 기억**의 경우 조지 밀러의 매직넘버 7에 따르면

**5개**에서 많아야 **9개** 밖에 저장을 못한다고 한다.

---

문제를 해결 하기 위해 단기 기억을 사용하는데, 
용량이 초과하면 **인지 부조화**가 생기기 마련이다.

<br>

과부하를 방지하기 좋은 방법은 **추상화** 이다.

---

**********************추상화는********************** 

- 불필요한 정보 제거
- 본질적인 정보만 남기기

<br>

일반적인 추상화는 문제의 크기를 줄이는 것.

→ 한 번에 해결하기 힘든 경우 더 작은 문제로 나눌 수 있다.

→ **분해(decomposition)** 라고 부른다

---

앞서 얘기한 단기 기억을 큰 추상화로 압축 시키면 단기 기억의 한계를 초월 할 수 있다.

특히 소프트웨어 개발의 경우 추상화와 분해를 통해 문제를 해결해야 된다.

---

## 프로시저 추상화와 데이터 추상화

현대적인 프로그래밍 추상화 메커니즘

1. **프로시저 추상화 (procedure abstraction)**
2. **데이터 추상화(data abstraction)**

<br>

**프로시저 추상화** 는 소프트웨어가 **무엇을 해야 하는지를** 추상화

**데이터 추상화**는 소프트웨어가 **무엇을 알아야 하는지를** 추상화

---

**프로시저 추상화** 로 분해 시 **기능 분해(functional decomposition)** , 알고리즘 분해

**데이터 추상화** 로 분해 시 데이터 중심으로.

1. 타입을 추상화, **추상 데이터 타입(ADT)**
2. 프로시저를 추상화,  **객체지향**

<br>

이렇듯 복잡성을 극복하는 방법은 **추상화 메커니즘**과 **분해 방법**을 이용해야 된다.

---

## 프로시저 추상화와 기능 분해

<br>

전통적인 기능 분해 방법으로 **하향식 접근법** 을 따른다.

<br>

<br>

**하향식 접근법**이란, 가장 최상위 기능을 정의하고, 점차 하위 기능으로 분해해 나가는 방법이다.

각 세분화 단계는 바로 위 단계보다 더 구체적이어야 한다.

---

![KakaoTalk_20230208_045350830](https://user-images.githubusercontent.com/55054505/217367341-e4728dff-b07f-40c2-9b2c-e59ec15f0244.jpg)


- 설계한 시스템은 트리(tree) 로 표현이 가능하다.
- 트리에서 각 노드(node)는 하나의 프로시저를 의미한다.

하향식 기능 분해는 논리적이고 체계적인 시스템 개발 절차를 제시를 합니다.

---

# 하향식 기능 분해의 문제점

<br>

- 시스템은 하나의 메인 함수로 구성되어 있지 않다.
<br>
- 기능 추가나 요구사항 변경으로 인해 메인 함수를 빈번하게 수정해야 한다.
<br>
- 비즈니스 로직이 사용자 인터페이스와 강하게 결합된다.
<br>
- 하향식 분해는 너무 이른 시기에 함수들의 실행 순서를 고정시키기 때문에 유연성과 재사용성이 저하된다.
<br>
- 데이터 형식이 변경될 경우 파급 효과를 예측할 수 없다.

---

하향식 설계와 관련된 모든 문제의 원인은 **결합도**다.
<br>

- 강한 결합도는 시스템 변경을 취학하게 만든다.
- 하향식 설계는 핵심 구조 함수들이 데이터와 강하게 결합되어 있다는 점이다.

---

### 언제 하향식 분해가 유용할까?

<br>

- 작은 프로그램과 개별 알고리즘
- 이미 해결된 알고리즘의 문서화

---

## 정보 은닉과 모듈

<br>

**기능 기반**으로 분해하는 것이 아니라, 

**변경의 방향**에 맞춰 시스템을 분해해야 한다.

<br>



- **모듈** 
: 책임의 할당
: 변경될 가능성이 있는 비밀은 내부로, 
: 잘 정의되서 쉽게 변경되지 않은 퍼블릭 인터페이스는 외부로.

- **정보 은닉** 
: 시스템을 모듈 단위로 분해하기 위한 기본 원리

---

**시스템을 모듈 단위로 어떻게 분해할 것인가?**

→ 감춰야하는 비밀을 찾고, 외부에서 내부의 비밀에 접근 못하도록 한다.

<br>

모듈은 2가지 비밀을 감춰야 된다.

1. **복잡성**
2. **변경 가능성**

가장 일반적인 비밀은 데이터이다.

---

# 모듈의 장점

---

**모듈 내부의 변수가 변경되더라도 모듈 내부에만 영향을 미친다.**

- 어떤 데이터가 변경됐을 때 검색할 수 있다.
- 데이터 변경으로 인한 파급효과를 제어가 가능하다.

---

**비즈니스 로직과 사용자 인터페이스에 대한 관심사를 분리한다.**

- 사용자 입력과 출력은 외부로.
- 비즈니스 로직은 모듈로.

---

**전역 변수와 전역 함수를 제거함으로써 네임스페이스 오염을 방지한다.**

- 이름 충돌의 위험을 완화한다.

---

모듈은 기능이 아니라 변경의 정도에 따라 시스템을 분해하게 한다.

각 모듈은 감춰야할 비밀의 집합이다.

따라서 모듈 내부는 **높은 응집도**를 유지한다.

모듈과 모듈 사이에서는 퍼블릭 인터페이스로 통신하기에, **낮은 결합도**를 유지한다.

---

# 모듈의 단점

인스턴스의 개념을 제공하지 않는다.

개별로 독립적인 단위로도 나눌 수 있어야 한다.

→ 추상화 데이터 타입

---

## 추상화 데이터 타입

타입 (type)

- 내용물의 종류
- 변수에 적용될 수 있는 연산의 가짓수

---

과거, 절차형 언어들은 적은 수의 내장 타입만 제공했으며, 새로운 타입을 추가하는 것이 제한되었다.

프로시저 추상화로는 한계가 있었다.

→ **데이터 추상화**라는 개념이 생겼다


추상 데이터 타입은 말 그대로 시스템 상태를 저장할 데이터만 표현한다.

핵심 로직은 추상 데이터 타입 외부에 있다.

---

## 클래스는 추상 데이터 타입인가?

클래스를 추상 데이터 타입이 틀린 설명은 아니다.

명확한 의미에서는 추상 데이터 타입과 클래스가 동일하지 않다.

<br>
큰 차이점으로 클래스는 상속과 다형성을 지원하지만,

추상 데이터 타입은 지원하지 않는다.

---

객체 지향 프로그래밍 (클래스) - 절차를 추상화

객체 기반 프로그래밍 (추상 데이터 타입) - 타입을 추상화

---

### 타입 추상화 vs 절차 추상화

<br>

타입 추상화의 대표적인 기법이 **추상 데이터 타입** 이다.

절차 추상화는 **객체 지향**이다.

`추상 데이터 타입`이 **오퍼레이션**을 기준으로 **타입**을 추상화 한다.

`객체지향`은 **타입**을 기준으로 **절차**들을 추상화 한다.

---


`추상 데이터 타입`의 경우 

새로운 타입을 추가해야 된다면 **클라이언트 조건문을 다 찾아서 수정해야 된다.**

`객체지향`의 경우 

타입 변수를 이용한 조건문을 **다형성**으로 대체한다.

즉, **새로운 로직을 추가하기 위해 클라이언트 코드를 수정할 필요가 없다.**

---

**개방-폐쇄 원칙 OCP(Open-Closed Principle)**

: 기존 코드의 아무런 영향을 미치지 않고 새로운 객체 유형과 행위를 추가할 수 있는 특성


**→ 변경하고 확장하기 쉬운 구조로 설계 가능.**


---


새로운 타입을 빈번하게 추가 → **객체지향**

새로운 오퍼레이션을 빈번하게 추가 → **추상 데이터 타입**

---

마지막으로,  협력이 중요하다.

객체지향에서 중요한 것은 역할, 책임, 협력이다.

<br>

객체가 참여할 협력을 결정하고, 

협력에 필요한 책임을 수행하기 위해

어떤 객체가 필요한지에 관한 고민을 해라.

<br>

그 책임을 다양한 방식으로 수행해야 할 때만 타입 계층 안에 각 절차를 추상화하라.

타입 계층과 다형성은 협력이라는 문맥 안에서 책임을 수행하는 방법에 관해 고민한 결과물이어야 하며 그 자체가 목적이 되서는 안 된다.