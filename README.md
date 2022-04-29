# MSA Ecommerce
- [MSA Ecommerce] Project Root
![main](https://user-images.githubusercontent.com/42602972/165476161-4c520bd6-0f48-4a85-90ee-65cfe7be9861.png)

## 프로젝트 구성
- Java 8
- Spring Boot(+Maven) 2.6.4
- Spring Data JPA 2.6.4
- Spring Security 2.6.4
- JWT jwtt 0.9.1
- Junit 5
- Spring Cloud 2021.0.1
  - Eureka 3.1.1    
  - Config 3.1.1
  - Gateway 3.1.1
  - Bus-amqp(RabbitMq) 3.1.1
  - Openfeign 3.1.1 
- H2(Embedded) 1.4.200  
- Docker <= 현재 진행중
	- RabbitMQ (완료)
	- MariaDB (완료)
	- Kafka(+Zookeper) (완료)
	- Zipkin
	- Prometheus
	- Grafana

## 구동방법
- ~~Docker RabbitMQ 설치~~
  - ~~docker run -d --name rabbitmq -p 5672:5672 -p 15672:15672 --restart=unless-stopped rabbitmq:management~~
  - 아래 '나주엥 추가할 작업 내용' 3번 진행 중
- Confing 로컬 저장소 생성      
  - **[Config-Server]** [참조](https://github.com/heom/MSA-Ecommerce-ConfigServer)
- 서비스 구동(아래 순서대로)
  - Config-Server
  - Discovery-Service
  - API-Gateway
  - User-Service / Order-Service / Catalog-Service

## 프로젝트 서비스 구성
- **[Config-Server]**
  - Github : [Source url](https://github.com/heom/MSA-Ecommerce-ConfigServer)
------------
- **[Config-Repository]**
  - Github : [Source url](https://github.com/heom/MSA-Ecommerce-Config)
------------
- **[Discovery-Service]**
  - Github : [Source url](https://github.com/heom/MSA-Ecommerce-DiscoveryService)
------------
- **[API-Gateway]**
  - Github : [Source url](https://github.com/heom/MSA-Ecommerce-ApiGateway)
------------
- **[User-Service]**
  - Github : [Source url](https://github.com/heom/MSA-Ecommerce-UserService)
------------
- **[Order-Service]**
  - Github : [Source url](https://github.com/heom/MSA-Ecommerce-OrderService)
------------
- **[Catalog-Service]**
  - Github : [Source url](https://github.com/heom/MSA-Ecommerce-CatalogService)

## 나중에 추가할 작업 내용
- 1. 각 서비스 인스턴스, 로드 밸런싱할 때 DB 동기화 미완 <= DB 앞에 Kafka(DB MQ) 사용할 예정
- 2. 장애처리/모니터링 기능 추가
- 3. CI/CD 기능 추가 <= Docker Container
- 4. 현재는 이벤트 드리븐 형식이 아닌, OpenFeign 활용한 가장 단순 msa 구조 <= Api Gateway 뒤에 Kafka(Event MQ) 사용할 예정
