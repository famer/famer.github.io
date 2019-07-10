---
title: Tying up microservices. Options overview.
---

Once system is decoupled to separate services question of interconnection of the rose up. Because as architect you have to make decision how clients and services will communicate with each other.

1. First solution named no solution at all: clients basically access microservices through preset entry points like prefixed ports and addresses. Advantage of this method no additional service to connect should be run. Disadvantages: since you have different entry points preset in every client and services, change of configuration of the structure will produce time consuming procedure of reconfiguration. And once your system has mobile applications which are not updated frequently, your company should be running previous version of configuration along with new for infinite time to make sure old users can use it. In addition you as a company do not have additional control over the traffic since it goes through different points.

2. So second option is to interconnect different services by means of extra service that will take control over traffic and be a public entry point.
Disadvantages: Need to have additional service and resources for it. Additional work and money for configuration and maintenance required. 
Advantages: Single entry point for public access and microservices  internal consumption. And ability to change internal configuration and structure of the system without influencing "public face". Solves the problem of mobile clients.
Possibility to load balance between instances for traffic.
Additional control over calls and possibility to modify requests and responses before sending it to services and back respectively.
Additional possibility to cache responses.

Once decided to follow second way, possibility to choose product for it appears.

### Nginx as reverse proxy

Idea of reverse proxy is exactly what is required: to collect resources from several servers on behalf of the client.

Solution is to redirect traffic based on some rules preset in nginx configuration. 
In respect of REST API those rules could be based on request path parts.

Example of nginx configuration.

    http {
    
        server {
           location /generic_sops/ {
              proxy_pass http://localhost:8084/v1/generic_sops/;
           }
          
           location /particular_sops/ {
              proxy_pass http://localhost:8085/v1/particular_sops/;
           }
      
        }
    }

Two microservices for `generic` and `particular` tied up. 
Nginx based on url part will redirect traffic to one or another microservice.

Advantages: Free and opensource in terms of expenses. Lightweight in terms of resources.
Provides additional features for load balancing and preventing attacks. 

Disadvantages: Nginx doesn't provide any possibility to modify and pipe requests and responses.

### Oracle Web Service Bus

Oracle Service Bus provides bus for connection services with additional features.
Interconnection of the API's made in GUI so it's quite native and easy.
In addition OSB provides possibility to modify requests and responses. Even in such a complicated way that part of request will go to one services other part of it will be filtered and go to other and response could be modified on its way as well.

Advantages: Additional control over traffic and it's modification. Wide range of formats supported. Graphical user interface.

Disadvantages: Relatively exacting for resources. No additional control over traffic balancing. 

### Event driven structure.

The idea behind it is to encapsulate in every single service ability to listen to events supplied by some messaging service(e.g. RabbitMQ). Every client posts request to Messaging service which caught by the client subscribed to the messaging bus.
Way doesn't really fit to ideology of current architecture of the several RESTful microservices decoupled by logic.
