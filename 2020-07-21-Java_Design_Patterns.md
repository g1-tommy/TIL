# Java Design Patterns

> ## Design Pattern
>
> - 좋은 코드 설계를 위한 설계 디자인 방법론
> - 응집도는 높이고, 결합도는 낮게, 요구사항 변경 시 코드 변경을 최소화하는 방향을 추구한다.
>
> 
>
> ## 객체지향 5대 원칙 (SOLID 원칙)
>
> ### SRP (Single Responsibility Principle - 단일 책임원칙)
>
> - 클래스나 함수는 단 하나의 책임(기능)만 가져야 함
>     - 클래스나 함수가 비대해지면 분리시킬 필요가 있다.
>
> ### OCP (Open-Closed Principle - 개방-폐쇄 원칙)
>
> - 기존 코드 변경에는 닫혀 있고, 추가 / 확장에는 열려 있어야 함
> - 자주 변경될 수 있는 내용은 수정하기 쉽게 설계하고, 자주 변경되지 않을 내용은 수정에 영향받지 않게 설계해야 함
>
> ### LSP (Liskov Substitution Principle - 리스코프 치환 원칙)
>
> - 자식 클래스는 부모 클래스에서 가능한 행위를 수행할 수 있어야 함
> - 파생 클래스를 만들 때, 정말 올바른 상속 관계를 갖는지 고려해야 함
>     - e.g. Rectangle, Square 클래스
>
> ### DIP (Dependency Inversion Principle - 의존 역전 원칙)
>
> - DI (Dependency Injection) 기술의 핵심
> - 의존 관계를 맺을 때, 변화하기 쉬운 것보다 변화하기 어려운 것에 의존해야 함
>     - 변화하기 쉬운 것 = 구체적인 것 (클래스, 서브 클래스 인스턴스)
>     - 변화하기 어려운 것 = 추상적인 것 (추상 클래스, 인터페이스)
>     - 즉 {인터페이스 / 추상클래스} {변수명} = {서브클래스 인스턴스} 꼴이 되어야 함
>
> ### ISP (Interface Segregation Principle - 인터페이스 분리 원칙)
>
> - 클라이언트가 자신이 이용하지 않는 메서드에 의존하지 않아야 함
> - 큰 덩어리의 인터페이스들을 구체적이고 작은 단위로 분리시킴으로써 클라이언트들이 꼭 필요한 메서드만 이용할 수 있게 함
>     - 인터페이스를 클라이언트에 특화되도록 분리시키는 것

## GoF

- Gang of Four (Erich Gamma, Richard Helm, Ralph Johnson, John Vissides) 에 의해 고안

![GoF](https://gmlwjd9405.github.io/images/design-pattern/types-of-designpattern.png)

1. Creational 패턴

    - 객체 생성에 관련된 패턴
    - 객체의 생성과 조합을 캡슐화해 특정 객체가 생성되거나 변경되어도 프로그램 구조에 영향을 크게 받지 않도록 유연성 제공

    - Abstract Factory
        - 구체적 클래스에 의존하지 않고 서로 연관되거나 의존적 객체들의 조합을 만드는 인터페이스를 제공하는 패턴
    - Factory Method
        - 객체 생성 처리를 서브 클래스로 분리해 처리하도록 캡슐화하는 패턴
    - Singleton
        - 전역 변수 사용하지 않고 객체를 하나만 생성하도록 하며, 생성된 객체를 어디에서든지 참조할 수 있도록 하는 패턴

2. Structural 패턴

    - 클래스나 객체를 조합해 더 큰 구조를 만드는 패턴
        - e.g. 서로 다른 인터페이스를 지닌 2개의 객체를 묶어 단일 인터페이스를 제공하거나 객체들을 서로 묶어 새로운 기능을 제공하는 패턴
    - Composite
        - 여러 개의 객체들로 구성된 복합 객체와 단일 객체를 클라이언트에서 구별 없이 다루게 해주는 패턴
    - Decorator
        - 객체 결합을 통해 기능을 동적으로 유연하게 확장할 수 있게 해주는 패턴

3. Behavioral 패턴

    - 객체나 클래스 사이의 알고리즘이나 책임 분배에 관련된 패턴
    - 한 객체가 혼자 수행할 수 없는 작업을 여러 개의 객체로 어떻게 분배하는지, 또 그렇게 하면서도 객체 사이의 결합도를 최소화하는 것에 중점을 둔다.
    - Observer
        - 한 객체의 상태 변화에 따라 다른 객체의 상태도 연동되도록 1:다 의존관계를 구성하는 패턴
    - State
        - 객체의 상태에 따라 객체의 행위 내용을 변경해주는 패턴
    - Strategy
        - 행위를 클래스로 캡슐화해 동적으로 행위를 자유롭게 바꿀 수 있게 해주는 패턴
    - Template Method
        - 어떤 작업을 처리하는 일부분을 서브 클래스로 캡슐화해 전체 일을 수행하는 구조는 바꾸지 않으면서 특정 단계에서 수행하는 내역을 바꾸는 패턴
    - Command
        - 실행될 기능을 캡슐화함으로써 주어진 여러 기능을 실행할 수 있는 재사용성이 높은 클래스를 설계하는 패턴