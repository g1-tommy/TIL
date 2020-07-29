# Design Pattern

## LSP

> Liskov Substitution Principle

- 자식 클래스는 부모 클래스에서 가능한 행위를 수행할 수 있어야 함
    - 자료형 S가 자료형 T의 하위형일 때, 필요한 프로그램 속성 (정확성, 수행 업무 등)의 변경 없이 자료형 T의 객체를 자료형 S의 객체로 치환할 수 있어야 함
- 파생 클래스를 만들때, 올바른 상속 관계를 갖는지 고려해야 함

### 위반 사례

```java
public class Execution {
  public static void main(String[] args) {
    SUV suv = new SUV();
    
    suv.fixAtTheCarCenter("SUV");
    suv.drivingOnTheRoad("SUV");
    suv.trafficRegulation("SUV");
    
    System.out.println();
    
    AsianaAirlines aa = new AsianaAirlines();
    aa.drivingOnTheRoad("aa");
    aa.fixAtTheCarCenter("aa");
    aa.trafficRegulation("aa");
  }
}
```

```java
public interface Car {
  void fixAtTheCarCenter(String obj);
  void drivingOnTheRoad(String obj);
  void trafficRegulation(String obj);
}
```

```java
public class AsianaAirlines implements Car {
  @Override
  public void fixAtTheCarCenter(String obj) {
    System.out.println(obj + "will be fixed when broken");
  }
  
  @Override
  public void drivingOnTheRoad(String obj) {
    System.out.println(obj + "will drive on the road");
  }
  
  @Override
  public void trafficRegulation(String obj) {
    System.out.println(obj + "should follow the regulation");
  }
}
```

```java
public class SUV implements Car {
	@Override
  public void fixAtTheCarCenter(String obj) {
    System.out.println(obj + "will be fixed when broken");
  }
  
  @Override
  public void drivingOnTheRoad(String obj) {
    System.out.println(obj + "will drive on the road");
  }
  
  @Override
  public void trafficRegulation(String obj) {
    System.out.println(obj + "should follow the regulation");
  }
}
```

> 위 코드에 따르면 로직 자체는 객체에 알맞게 구현되었을지 모르나 전혀 해당되지 않는 관계를 맺고 있는 상황이다.