# [AWS] Lambda / API Gateway

> References
>
> - [44bits](https://www.44bits.io/ko/keyword/aws-lambda)
> - [Medium](https://medium.com/harrythegreat/비전공자를-위한-aws-lambda-1편-5697cee473eb)
> - [Medium](https://medium.com/@kyh980909/aws-lambda란-무엇인가-229e0cf233ee)

## Lambda

> `FaaS` (Function as a Service)
>
> Serverless Computing Service로 애플리케이션 실행을 위한 별도 서버 셋업 없이 곧바로 코드 실행이 가능하도록 함
>
> -> Provisioning (사용자 요구에 맞는 시스템 자원 할당/배치/배포 후 필요시 시스템을 즉시 사용한 상태로 준비하는 것)이나 관리 필요 없이 코드 실행이 가능하게끔 해주는 컴퓨팅 서비스
>
> - Serverless
>     - ![Serverless](https://miro.medium.com/max/700/1*zOIMutM07rfvLibZvOSgfQ.jpeg)

- (2020. 2 현재) Java, Javascript, Go, C#, Powershell, Python, Ruby 언어 지원, 공식 런타임 없어도 커스텀 런타임 통해 지원하지 않는 언어를 사용할 수 있게 확장 가능하며, 리눅스에서 실행가능한 임의 바이너리 포함 실행 또한 가능
- Event-Driven 방식으로 동작
- 필요시에만 코드가 동작하며, 하루에 몇 개 요청에서 초당 수천 개 요청까지 자동 확장 가능
- 사용한 컴퓨팅 시간에 한해 요금 지불
- API Gateway, Elastic Load Balancer의 HTTP 요청 처리, S3 Object, DynamoDB, Kinesis에서 발생하는 이벤트를 트리거로 실행 가능
- Container는 지원하지 않음 (컨테이너 기반 서버리스 서비스는 `Fargate` 이용)

![Benefits](https://miro.medium.com/max/700/1*5Tjlqyd-mMJS39uwIDXEcg.png)

### Extensions / Related Services

- Lambda Edge

    - CloudFront에서 제공하는 기능으로 CloudFront Edge 상에서 Lambda 함수 실행

        > - CloudFront Edge
        >     - CDN 파일 전송하는 캐시 서버 - Region보다 훨씬 다양한 위치에 존재

        - 헤더 조작, SEO, 실시간 이미지 변환 등 용도로 사용되며 일반 Lambda 함수보다 실행 시간 및 리소스 제약

- Lambda Layers
    - 공통된 부분을 레이어로 만들고 함수들 간에 공유해서 사용할 수 있음

- Provisioned Concurrency
    - Cold Start 문제 해결을 우해, 미리 Lambda 함수를 실행할 수 있도록 준비해두는 기능
- Step Functions
    - Lambda 함수를 조합해 Workflow를 구성하는 서비스
    - ASL(Amazon States Language)로 작성된 Workflow(State Machine)을 실행하며, Lambda를 비롯해 Batch, SNS, SQS, DynamoDB 등 다양한 서비스와 통합해서 사용
- RDS Proxy
    - Client와 RDS Database 사이에서 Connection을 관리해주는 서비스
    - Database를 조작하는 Lambda Function이 갑작스런 요청 증가로 Connection 수가 급격히 증가할 때 Database 메모리 부족 등의 문제가 발생할 수 있는데 RDS Proxy를 통해 문제 완화
- Framework
    - AWS Serverless Application Model
    - Zappa of Python
    - Jets of Ruby
    - Serverless of Node.js
    - Apex

### Issues

![Issues](https://miro.medium.com/max/700/1*h_5CW6intkMKuuTP9hzZTA.png)

### Case

[이미지 썸네일 생성 개발 후기 - 당근마켓](https://medium.com/daangn/aws-lambda%EB%A5%BC-%EC%9D%B4%EC%9A%A9%ED%95%9C-%EC%9D%B4%EB%AF%B8%EC%A7%80-%EC%8D%B8%EB%84%A4%EC%9D%BC-%EC%83%9D%EC%84%B1-%EA%B0%9C%EB%B0%9C-%ED%9B%84%EA%B8%B0-acc278d49980)

![Case Example 1](https://miro.medium.com/max/564/1*6DWQZjgH_e8RmE4gjOF0Kg.png)

![Case Example 2](https://miro.medium.com/max/566/1*hygn6d3MtsBMoZ_VctW0Xg.png)

![Case Example 3](https://miro.medium.com/max/572/1*Uvm1Eo6viOqe1f2A025vMw.png)

## API Gateway

- 개발자가 API를 생성, 게시, 유지관리, 모니터링 및 보호할 수 있게 하는 AWS 서비스
- EC2에서 실행되는 Workload, Lambda에서 실행되는 코드, 기타 웹 애플리케이션 등과 같은 백엔드 서비스 데이터, 비즈니스 로직 또는 기능에 애플리케이션이 액세스하게 해주는 "현관문" 역할하는 API 생성 가능

