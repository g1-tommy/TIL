# Design Pattern

## DIP

> Dependency Inversion Principle

- 의존 관계를 맺을 때, 변화하기 쉬운 것보다 변화하기 어려운 것에 의존해야 함
    - 변화하기 쉬운 것 = 구체적인 것 (클래스, 서브 클래스 인스턴스)
    - 변화하기 어려운 것 = 추상적인 것 (추상 클래스, 인터페이스)
    - 즉 {인터페이스 / 추상클래스} {변수명} = {서브클래스 인스턴스} 꼴이 되어야 함
- 상위 계층이 하위 계층에 의존하는 전통적 의존 관계를 반전시켜 상위 계층이 하위 계층의 구현으로 독립되게 할 수 있다.
- 상위 모듈은 하위 모듈에 의존해서는 안되며, 상위 / 하위 모듈 모두 추상화에 의존해야 한다.
- 추상화는 세부 사항에 의존하면 안 되며, 세부사항이 추상화에 의존해야 함



### Example

```java
public class Execution {
  public static void main(String[] args) {
    HomeAppliance ha = new Notebook();
    Person p = new Person();
    
    person.setHomeAppliance(ha);
    person.use();
  }
}
```

```java
public class Person {
  private HomeAppliance ha;
  
  public void setHomeAppliance(HomeAppliance ha) {
    this.ha = ha;
  }
  
  public void use() {
    System.out.println(ha.toString());
  }
}
```

```java
public abstract class HomeAppliance {}
```

```java
public class Notebook extends HomeAppliance {
  public String toString() {
    return "Notebook";
  }
}
```

```java
public class TV extends HomeAppliance {
  public String toString() {
    return "TV";
  }
}
```

```java
public class Refridgerator extends HomeAppliance {
  public String toString() {
    return "Refridgerator";
  }
}
```

> 사람이 사용하고자하는 가전기기의 객체 타입을 변경하면 해당 객체가 출력될 것 (HomeAppliance의 하위형), 따라서 기존 코드에 영향을 받지 않는다.