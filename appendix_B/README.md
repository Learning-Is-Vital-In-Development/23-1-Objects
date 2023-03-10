# B. ****타입 계층의 구현****

### 타입 : 개념의 분류

### 클래스 : 타입을 구현하는 한 가지 방법

유의할 점

- 타입 계층은 동일한 메시지에 대한 행동 호환성을 전제로 하기 때문에

타입계층을 구현하는 방법인 동시에 다형성을 구현하는 방법이다.

- 타입과 타입 계층을 구현한다고 해서 서브타이핑의 관계가 보장되는 것은 아니다.

→  리스코프 치환 원칙을 준수해야됨

## 클래스를 이용한 타입 계층 구현

타입은 객체의 public interface를 가리키기 때문에

클래스는 객체의 타입과 구현을 동시에 정의함

객체 지향에서 클래스는 **사용자 지정 타입** 이라고도 불림

타입을 구현할 수 있는 다양한 방법이 존재하는 순간 부터는

클래스와 타입은 갈라지기 시작함

만약 A와 퍼블릭 인터페이스는 동일하지만 다른 방식으로 구현해야되는 객체가 필요하면 

A와 동일한 타입으로 분류되는 객체가 필요한 것이다.

퍼블릭 인터페이스를 유지하면서 새로운 구현을 가진 객체를 추가할 수 있는 방법은

**상속**이다.

### 결국 클래스는 타입을 구현할 수 잇는 다양한 방법 중 하나일 뿐이다.

## 인터페이스를 이용한 타입 계층 구현

자바는 다중상속이 불가능하기에,

인터페이스를 이용해 타입을 정의하고

클래스를 이용해 객체를 구현하면

상속을 사용하지 않고 타입 계층을 구현할 수 있다.

1. 여러 클래스가 동일한 타입을 구현할 수 있다.
2. 하나의 클래스가 여러 타입을 구현할 수 있다.

**객체의 구현은 다를지라도 인터페이스는 같을 수 있다.**

### 클래스와 타입의 차이점

- 타입
    - 동일한 퍼블릭 인터페이스를 가진 객체들의 범주
- 클래스
    - 타입에 속하는 객체들을 구현하기 위한 구현 메커니즘

객체 지향에서 중요한 것은 `협력` 안에서 객체가 제공하는 `행동`이라는 사실을 기억하자

## 추상 클래스를 이용한 타입 계층 구현

구체 클래스로 타입 정의해서 상속하는 방법

추상 클래스토 타입 정의해서 상속하는 방법

차이점은 

- 추상화의 정도
- 상속을 사용하는 의도

## 추상클래스와 인터페이스 결합하기

대부분 객체 지향들은 단일 상속만 지원함

인터페이스는 중복 코드를 제거하기 힘듦

인터페이스를 이용해 타입을 정의하고

특정 상속 계층에 국한된 코드를 공유할 필요가 있을 경우에는

추상 클래스를 이용해 코드 중복을 방지하는 것임

이러한 방식을 **골격 구현 추상 클래스**라고 함

장점

1. 다양한 구현 방법이 필요할 경우 추상 클래스를 추가해서 쉽게 해결이 가능함
2. 이미 부모 클래스가 존재하는 클래스라고 하더라도 인터페이스를 추가함으로써 새로운 타입을 쉽게 확장할 수 있음.

## 덕 다이핑

> "If it walks like a duck and it quacks like a duck, then it must be a duck”
> 

오리처럼 걷고 소리내면 그건 분명 오리라고 결정한다.

주로 동적 타입 언어에서 사용하는 방법이다.

```java
// JAVA
String name = "abc";

// Javascript
const name = "abc";
```

우리는 자바를 정적 타입 언어, 자바스크립트를 동적 타입 언어라고 분류할 수 있다.

정적은 컴파일 시점, 동적은 런타임 시점에 타입이 체크되어진다고 생각하면 된다.

- 덕 다이핑을 사용하면 메시지 수준으로 결합도를 낮출 수 있기 때문에 유연한 설계가 가능하다.
- 하지만 컴파일 시점에서 발견할 수 있는 오류를 실행 시점에서 미뤄서 코드 안정성이 떨어진다.

```jsx
// static 타입 스크립트
let staticName: string = "abc";
staticName = 1; // TypeError

// dynamic 자바 스크립트
let dynamicName = "abc";
dynamicName = 1; // Ok
```

- 타입 스크립트는 기존에 자바스크립트가 가지던 런타임에서 오는 이슈들을 컴파일 시점에 알아차릴 수 있다.

## 믹스인과 타입 계층

**믹스인은**

객체를 생성할 때 코드 일부를 섞어 넣을 수 있도록 만들어진 일종의 추상 서브 클래스이다.

언어마다 차이점은 있지만, 동일한 `행동` 을 중복 코드 없이 재사용할 수 있게 만드는 것이다.

믹스인을 통한 재사용성 → 객체들은 동일한 행동을 함 → 공통된 행동이 믹스인된 객체들은 동일한 메시즈를 수신할 수 있는 퍼블릭 인터페이스를 공유하게 됨 

- 대부분 믹스인을 구현하는 기법은 타입을 정의함

자바에서는 믹스인을 구현하기 위해 **디폴트 메서드**를 사용함

- 간결한 인터페이스를 가진 클래스를 풍부한 인터페이스를 가진 클래스로 변경이 가능함

그러나 문제점이 있음

1. 인터페이스를 구현하는 모든 클래스들이 해당 메서드의 구현을 제공해야 됨
2. 퍼블릭 메서드로 구현되어 있기에 외부로 노출할 필요가 없는 메서드를 불필요하게 퍼블릭 인터페이스에 추가하게 됨
3. 인터페이스가 불필요하게 비대해지고 캡슐화가 약해짐

자바 8에 추가된 디폴트 메서드를 추가한 이유는

인터페이스로 추상 클래스의 역할을 대체하라는 것이 아님.

기존에 널리 사용되고 있는 인터페이스에 새로운 오퍼레이션을 추가할 경우 발생하는

하위 호환성 문제를 해결하기 위해서임.

타입을 정의하기 위해 디폴트 메서드를 사용할 생각이라면 한계를 알아야 됨.

### 결론

어떤 방법을 사용해서 타입 계층을 구현했다고 해서 모든 타입 구현체들이 서브 타입과 슈퍼 타입을 조건을 만족시키는 것은 아님

타입 계층을 구현한다고 하더라도 리스코프 치환 원칙을 지켜야 됨.