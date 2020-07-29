# Design Pattern

## ISP

> Interface Segregation Principle

- 클라이언트가 자신이 이용하지 않는 메서드에 의존하지 않아야 함
- 큰 덩어리 인터페이스를 구체적인 작은 단위로 분리시켜 클라이언트가 필요한 메서드만 이용하도록 해야 함
    - 인터페이스를 클라이언트에 특화되도록 분리시키는 것

### Example

![Before](https://t1.daumcdn.net/cfile/tistory/99FBCC3359C49E0119)

> Before

![After](https://t1.daumcdn.net/cfile/tistory/9954CE3359C49E0214)

> After

