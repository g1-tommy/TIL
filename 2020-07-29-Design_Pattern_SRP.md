# Design Pattern

## SRP

> Single Responsibility Principle

- 하나의 클래스에 하나의 책임만을 부여
    - 클래스나 함수가 비대해지면 분리 필요



### 위반 사례

```java
public class User {
  private String userName;
  private int userAge;
  private String userGender;
  private String userAddress;

 	public void userRegistration() {}// User에 User 이상의 책임이 부여됨 (위반)
  public void membershipLevel() {} // User에 User 이상의 책임이 부여됨 (위반)
}
```

### SRP 적용

```java
public class User {
  private String userName;
  private int userAge;
  private String userGender;
  private String userAddress;
}
```

```java
public class Membership {
  public void membershipLevel(User user) {
    // Print Membership Level
  }
}
```

```java
public class Registration {
  public void userRegistration(User user) {
    // Register New User
  }
  
  public void registrationCost(User user) {
    // Print Registration Cost
  }
}
```





