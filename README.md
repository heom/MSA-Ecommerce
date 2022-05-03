# MSA Ecommerce
- [MSA Ecommerce] Project Root
![UpdateBase](https://user-images.githubusercontent.com/42602972/166440790-87bf2d23-4669-481a-b3e7-08b0246cf26b.png)

## 프로젝트 구성
- Java 8
- Spring Boot(+Maven) 2.6.4
- Spring Data JPA 2.6.4
- Spring Security 2.6.4
- Spring Actuator 2.6.4
- JWT jwtt 0.9.1
- Junit 5
- Spring Cloud 2021.0.1
  - Eureka 3.1.1    
  - Config 3.1.1
  - Gateway 3.1.1
  - Bus-amqp(RabbitMq) 3.1.1
  - Openfeign 3.1.1 
  - Resilience4j 2.1.1
  - Sleuth 3.1.1
  - Zipkin 2.2.3 
- H2(Embedded) 1.4.200  
- Docker
	- RabbitMQ
	- Kafka(+Zookeper)
	- Zipkin
	- Prometheus
	- Grafana

## 구동방법
- Confing 로컬/원격 저장소 생성      
  - **[Config-Server]** [참조](https://github.com/heom/MSA-Ecommerce-ConfigServer)
- Docker 프로젝트 환경 Docker Container 실행(아래 순서대로)
  - **[Docker 프로젝트 환경 구성방법]** [참조](https://github.com/heom/MSA-Ecommerce/blob/master/Docker%20%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20%ED%99%98%EA%B2%BD%20%EA%B5%AC%EC%84%B1%EB%B0%A9%EB%B2%95.md)
	- Network 설정
	- RabbitMQ
	- Kafka(+Zookeper)
	- Zipkin
	- Prometheus
	- Grafana
- 서비스 구동(아래 순서대로)
  - Config-Server
  - Discovery-Service
  - API-Gateway
  - User-Service / Order-Service / Catalog-Service
![Dockers](https://user-images.githubusercontent.com/42602972/166441188-d6e6ddf3-c77f-4757-9b64-05d24af51b5a.png)

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

## URL
- **[Zipkin]**
  - [DashBoard Link](http://localhost:9411/zipkin/)
- **[Prometheus]**
  - [DashBoard Link](http://localhost:9090/)
- **[Grafana]**
  - [DashBoard Link](http://localhost:3000/login)

## 추가 작업 중인 내용
- 1. 서비스 인스턴스간 MQ(Kafka) 적용 - **완료**
- 2. 서비스 인스턴스간 조회 OpenFeign 장애처리 Resilience4j 적용 - **완료**
- 3. 서비스 인스턴스간 분산 추적을 위한 Zipkin 적용 - **완료**
- 4. 서비스 모니터링을 위한 Prometheus/Grafana 적용 - **완료**
- 5. Local -> Docker 환경 변경 - **완료**
- 6. DevOps를 위한 CI/CD 구축
- 7. Microservice Architecture와 Patterns
- 8. WebFlux를 이용한 Reactive RESTful API 

