# Prudential POC Documentation



## Application Structure
![image](https://user-images.githubusercontent.com/103875790/173271480-0eb16dc6-4afc-4d5d-a436-07a0975c9c65.png)


### Cloud API Gateway

* Description: This is a single entry & exit point to multiple microservices for an external application/client. Sometimes it is also called Edge Microservice. Since external clients are restricted to access the microservices directly, it acts as a mediator between external clients & the collection of microservices.
* Port: ```9191```
* Repository: [https://github.com/aritraibm/cloud-gateway.git](https://github.com/aritraibm/cloud-gateway.git)
* Branch: ```master```


### JWT

* Description: For authentication/ authorization, the microservice would need the JWT access token to be passed to it. It can then verify the JWT token & extract the user roles from the claims & accordingly allow/deny the request for the concerned endpoint. (As of now, POC is done, however the implementation is pending).
* Port: ```NA```
* Repository: ```NA```
* Branch: ```NA```


### Service Registry/Discovery

* Description: It is used to keep track of the available instances of each microservice in an application. Here we are tracking below instance as a part of service registry.
* Port: ```8761```
* Repository: [https://github.com/aritraibm/service-registry.git](https://github.com/aritraibm/service-registry.git)
* Branch: ```master```


### Cloud Configuration Server

* Description: Spring Cloud Config provides server and client-side support for externalized configuration in a distributed system. With the Config Server you have a central place to manage external properties for applications across all environments.
* Port: ```9296```
* Repository: [https://github.com/aritraibm/cloud.config.server.git](https://github.com/aritraibm/cloud.config.server.git)
* Branch: ```master```


### User Service

* Description: User service is a standalone microservice which is responsible to provide user details to Rest clients, it internally calls Department service thru Rest Template (however we can use feign also). We can get the various way (default JPA, JPQL, SQL) to interact with database.
* Port: ```9092```
* Repository: [https://github.com/aritraibm/user.service.git](https://github.com/aritraibm/user.service.git)
* Branch: ```master```


### Department Service

* Description: Department service is also a standalone microservice which is responsible to provide department details to Rest clients and user service.
* Port: ```9091```
* Repository: [https://github.com/aritraibm/department.service.git](https://github.com/aritraibm/department.service.git)
* Branch: ```master```


## Distributed Logging Implementation

### ELK Stack (with Sleuth)

* Description: To implement distributed logging, we can use Logstash, Elastic Search, and Kibana. Sleuth will help us to generate and maintain a global trace or correlation id for all the required applications. Logstash will collect the logs from the application and provide them into elastic search and Kibana helps us to visualize (as it provides us an interactive UI to view) the logs.
Here, we used ELK with the 7.6.2 version as it’s compatible with jdk8, however, we can use any of the updated versions with updated JDK. Sleuth dependency is available in user service pom.xml and below are the download link for all of the ELK applications.

* ElasticSearch: https://www.elastic.co/downloads/elasticsearch

* Logstash: https://www.elastic.co/downloads/logstash

* Kibana: https://www.elastic.co/downloads/kibana


### Zipkin & Rabbit (with Sleuth)

* Description: Zipkin is also a very good way to maintain/ view the distributed logs. Here also, Sleuth will help us to generate and maintain a global trace or correlation id for all the required applications. It’s recommended to integrate Zipkin with rabbit (MQ) to avoid single failure scenarios.


## Functionalities & Endpoints

### Save Department Details

* Description: This API will save new department details.
* URL: ```http://localhost:9191/pru-dept/save-dept```
* HTTP method: ```POST```
* Body: 
```
{
    "deptName": "IT",
    "deptAddress": "India",
    "deptCode": "D-001"
}
```


### Get Department Details by Department Id

* Description: This API will get existing department details by department Id.
* URL: ```http://localhost:9191/pru-dept/get-dept/4```
* HTTP method: ```GET```
* Body: 
```
NA
```



### Save User Details

* Description: This API will save new user details.
* URL: ```http://localhost:9191/pru-user/save-user```
* HTTP method: ```POST```
* Body: 
```
{
    "firstName": "Alex",
    "lastName": "Nichols",
    "email": "alex@test.com",
    "deptId": 4
}
```



### Get User Details by User Id (JPA method)

* Description: This API will get existing user details by user Id.
* URL: ```http://localhost:9191/pru-user/get-user/5```
* HTTP method: ```GET```
* Body: 
```
NA
```



### Get User Details by User Id (Named Native - SQL)

* Description: This API will get existing user details by user Id.
* URL: ```http://localhost:9191/pru-user/get-user-by-named-native/5```
* HTTP method: ```GET```
* Body: 
```
NA
```



### Get User Details by User Id (Named - JPQL)

* Description: This API will get existing user details by user Id.
* URL: ```http://localhost:9191/pru-user/get-user-by-named/5```
* HTTP method: ```GET```
* Body: 
```
NA
```


## Version History

* v1.0.0
    * Initial Release
