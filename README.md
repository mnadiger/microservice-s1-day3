# microservice-s1-day3
Actuator: (Ops - Spring Boot), Dynamic Registration and Discovery to our microservice: (storeapp)
Day 3:

Actuator: (Ops - Spring Boot)

1) Starter:

<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-actuator</artifactId>
</dependency>

2) Endpoints:

Enable all the endpoints:

In application.properties:
management.endpoints.web.exposure.include=*


------

Environment env;

http://localhost:8080/actuator/env

-------------------------------------------------------

2 Solution:

1) After restart
2) Refresh endpoint (Actuator) - Trigger

"http://localhost:8080/actuator/refresh"
- POST - POSTMAN

-------------------------------------------------------

Refresh - Multiple Microservices
- Spring Cloud Bus

-------------------------------------------------------

Server.port=0
- dynamic port

How consumers knows the service port?
- Dynamic Port

Cloud: EC2
- Dynamic IP

- Number of Instances

Service-to-service call
????

-------------------------------------------------------

https://microservices.io/

https://microservices.io/patterns/service-registry.html

Netflix Eureka service registry

https://microservices.io/patterns/self-registration.html

-------------------------------------------------------

Eureka Server:

1) Setting up the Eureka Server: (cloudserver-eureka)

1.1) Create a project with starters - Eureka Server, Actuator

1.2) In application.properties:

server.port=8761
eureka.client.register-with-eureka=false
eureka.client.fetch-registry=false

management.endpoints.web.exposure.include=*

1.3) Add @EnableEurekaServer on the Application class

1.4) Check http://localhost:8761

----------------------------------

2) Enable Dynamic Registration and Discovery to our microservice: (storeapp)

2.1) Add the Starter 
- 
<dependency>
<groupId>org.springframework.cloud</groupId>
<artifactId>spring-cloud-starter-netflix-eureka-client</artifactId>
</dependency>

2.2) In application.properties:

eureka.client.serviceUrl.defaultZone=http://localhost:8761/eureka

spring.application.name=product-service

2.3) Add @EnableEurekaClient on the Application class

----------------------------------

Start the Config Server
Start the Eureka Server
Start the storeapp (Product Service)

----------------------------------
