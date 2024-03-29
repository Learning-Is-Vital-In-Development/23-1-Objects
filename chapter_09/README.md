---
marp: true

---

# Ch9 : 유연한 설계

---

# 개방-폐쇄 원칙

소프트웨어 개체(클래스, 모듈, 함수 등등)는 확장에 대해 열려 있어야 하고,
수정에 대해서는 닫혀 있어야 한다.

---

# 개방-폐쇄 원칙

* 확장에 대해 열려 있다. : 애플리케이션의 요구사항이 변경될 때 변경에 맞게 새로운 동작을 추가해서 애플리케이션의 기능을 확장할 수 있다.
* 수정에 대해 닫혀 있다. : 기존의 코드를 수정하지 않고도 애플리케이션의 동작을 추가하거나 변경할 수 있다.

---

# 의존성

개방-폐쇄 원칙은 런타임 의존성과 컴파일타임 의존성에 관한 이야기다.
즉, 유연하고 재사용 가능한 설계를 위해 런타임 의존성과 컴파일타임 의존성은 서로 다른 구조를 가져야한다.

---

# 추상화

개방-폐쇄 원칙의 핵심은 **추상화에 의존하는 것**이다.

추상화 : 핵심적인 부분만 남기고 불필요한 부분은 생략함으로써 복잡성을 극복하는 기법

* 핵심적인 부분(컴파일타임 의존성)
* 불필요한 부분(런타임 의존성)

---

# 생성 사용 분리

* 결합도가 높아질수록 개방-폐쇄 원칙을 따르는 구조를 설계하기 어려워진다.
* 객체 생성에 대한 지식은 과도한 결합도를 초래하는 경향이 있다.

유연하고 재사용 가능한 설계를 원한다면 객체와 관련된 생성, 사용을 분리해야 한다.

---

# 객체 분해

* 표현적 분해 : 도메인에 존재하는 사물 또는 개념을 표현하는 객체들을 이용해 시스템을 분해
* 행위적 분해 : 도메인이 아닌 설계자가 편의를 위해 임의로 만든 객체를 이용해 시스템을 분해


---

# 의존성 주입

* 생성자 주입 : 객체를 생성하는 시점에 생성자를 통한 의존성 해결
* setter 주입 : 객체 생성 후 setter 메서드를 통한 의존성 해결
* 메서드 주입 : 메서드 실행 시 인자를 이용한 의존성 해결

---

# 숨겨진 의존성

숨겨진 의존성은 캡슐화를 위반한다.
-> 의존성을 이해하기 위해 코드의 내부 구현을 이해할 것을 강요

의존성 주입을 통해 이 문제를 해결할 수 있다.

명시적 의존성이 숨겨진 의존성보다 좋다.

(스프링에서 제공해주는 IOC을 통해 의존성을 쉽게 해결할 수 있다.)

---

# 의존성 역전 원칙(Dependency Inversion Principle, DIP)

* 상위 수준의 모듈은 하위 수준의 모듈에 의존해서는 안 된다. 둘 모두 추상화에 의존해야 한다.
* 추상화는 구체적인 사항에 의존해서는 안 된다. 구체적인 사항은 추상화에 의존해야 한다.

---

# 의존성 역전 원칙(Dependency Inversion Principle, DIP)

의존성 원칙에 따라 상위 수준의 협력 흐름을 재사용하기 위해서는 추상화가 제공하는 인터페이스의 소유권 역시 역전시켜야 한다.

유연하고 재사용 가능하며 컨텍스트 독립적인 설계는 전통적인 패러다임이 고수하는 의존성의 방향을 역전시킨다.

* 전통적인 패러다임 : 상위 수준 모듈이 하위 수준 모듈 의존, 인터페이스가 하위 수준 모듈에 속함.

* 체지향 패러다임 : 상위 수준 모듈과 하위 수준 모듈이 모두 추상화에 의존, 인터페이스가 상위 수준 모듈에 속함.


---

# 유연한 설계

유연하고 재사용 가능한 설계가 항상 좋은 것은 아니다.
유연한 설계는 복잡한 설계를 낳는다. 하지만 유연하지 않은 설계는 단순하고 명확하다.
유연성은 코드를 읽는 사람들이 복잡함을 수용할 수 있을 때만 가치가 있다.

---

# 협력과 책임

객체의 협력과 책임이 중요하다.
설계를 유연하게 만들기 위해서는 먼저 역할, 책임, 협력에 초점을 맞춰야 한다.
