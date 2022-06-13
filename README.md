# Prudential POC Documentation

Simple overview of use/purpose.

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


### Cloud API Gateway

* Description: This is a single entry & exit point to multiple microservices for an external application/client. Sometimes it is also called Edge Microservice. Since external clients are restricted to access the microservices directly, it acts as a mediator between external clients & the collection of microservices.
* Port: ```9191```
* Repository: [https://github.com/aritraibm/cloud-gateway.git](https://github.com/aritraibm/cloud-gateway.git)
* Branch: ```master```
### Installing

* How/where to download your program
* Any modifications needed to be made to files/folders

### Executing program

* How to run the program
* Step-by-step bullets
```
code blocks for commands
```

## Help

Any advise for common problems or issues.
```
command to run if program contains helper info
```

## Authors

Contributors names and contact info

ex. Dominique Pizzie  
ex. [@DomPizzie](https://twitter.com/dompizzie)

## Version History

* 0.2
    * Various bug fixes and optimizations
    * See [commit change]() or See [release history]()
* 0.1
    * Initial Release

## License

This project is licensed under the [NAME HERE] License - see the LICENSE.md file for details

## Acknowledgments

Inspiration, code snippets, etc.
* [awesome-readme](https://github.com/matiassingers/awesome-readme)
* [PurpleBooth](https://gist.github.com/PurpleBooth/109311bb0361f32d87a2)
* [dbader](https://github.com/dbader/readme-template)
* [zenorocha](https://gist.github.com/zenorocha/4526327)
* [fvcproductions](https://gist.github.com/fvcproductions/1bfc2d4aecb01a834b46)
