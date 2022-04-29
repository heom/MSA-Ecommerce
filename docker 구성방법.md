Network
	- docker network create --gateway 172.18.0.1 --subnet 172.18.0.0/16 ecommerce-network

RabbitMQ 
	- docker run -d --network ecommerce-network -p 15672:15672 -p 5672:5672 -p 15671:15671 -p 5671:5671 -p 4369:4369 -e RABBITMQ_DEFAULT_USER=guest -e RABBITMQ_DEFAULT_PASS=guest --name rabbitmq rabbitmq:management

MariaDB
	* Dockerfile_mariadb 다운로드 필요 <= 다운로드 경로에서 작업 필요
	- docker build -t ccs159/my-mariadb:1.0 -f Dockerfile_mariadb .
    - docker run -d --network ecommerce-network -p 3307:3306 --name mariadb ccs159/my-mariadb:1.0
	
ConfigServer
	* 프로젝트 Root에 Dockerfile 존재 <= 프로젝트 Root에서 작업 필요
	- docker build -t ccs159/config-service:1.0 .
	- docker push ccs159/config-service:1.0
	- docker run -d -p 8888:8888 --network ecommerce-network -e "spring.rabbitmq.host=rabbitmq" -e "spring.profiles.active=default" --name config-service ccs159/config-service:1.0
	
DiscoveryService
	* 프로젝트 Root에 Dockerfile 존재 <= 프로젝트 Root에서 작업 필요
	- docker build -t ccs159/discovery-service:1.0 .
	- docker push ccs159/discovery-service:1.0
	- docker run -d -p 8761:8761 --network ecommerce-network -e "spring.cloud.config.uri=http://config-service:8888" -e "spring.rabbitmq.host=rabbitmq" --name discovery-service ccs159/discovery-service:1.0
	
APIGatewayServer
	* 프로젝트 Root에 Dockerfile 존재 <= 프로젝트 Root에서 작업 필요
	- docker build -t ccs159/apigateway-service:1.0 .
	- docker push ccs159/apigateway-service:1.0
	- docker run -d -p 8000:8000 --network ecommerce-network -e "spring.cloud.config.uri=http://config-service:8888" -e "spring.rabbitmq.host=rabbitmq" -e "eureka.client.serviceUrl.defaultZone=http://discovery-service:8761/eureka/" --name apigateway-service ccs159/apigateway-service:1.0
	

	