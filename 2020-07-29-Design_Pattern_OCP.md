# Design Pattern

## OCP

> Open-Closed Principle

- 확장에는 개방되고, 수정에는 닫힌다
    - 기존 코드는 변경하지 않고 기능을 추가함을 의미
    - 자주 변경될 수 있는 내용은 수정하기 쉽게 설계하고, 자주 변경되지 않을 내용은 수정에 영향받지 않도록 설계해야함

### OCP 위반

```java
public class Circle {
  public double radius;
}
```

```java
public class Rectangle {
  public double width;
  public double height;
}
```

```java
public class Calculation {
  public double calcCircle(Circle circle) {
    return circle.radius * circle.radius / 3.14;
  }
  
  public double calcRect(Rectangle rect) {
    return rect.width * rect.height;
  }
}
```

> 기존에 Calculation 클래스에 calcCircle만 존재하다, calcRect가 추가 (확장 및 기존 코드의 변경)

### 해결

```java
public interface Figure {
  public double calculator();
}
```

```java
public class Circle implements Figure {
  public double radius;
  
  @Override
  public double calculator() {
    return radius * radius / 3.14;
  }
}
```

```java
public class Rectangle implements Figure {
  public double width;
  public double height;
  
  @Override
  public double calculator() {
    return width * height;
  }
}
```

```java
public class Calculation {
  public double CalculatorFigure(Figure figure) {
    return figure.calculator();
  }
}
```

```java
public class Execution {
	public static void main(String[] args) {
    Calculation calculation = new Calculation();
    calculation.CalculatorFigure(new Circle());
  }	
}
```

> 도형의 기본체가 되는 Figure Interface를 정의하여 각 도형은 해당 interface를 implement하며 추가되는 코드가 다른 클래스에서는 발생되지 않음

