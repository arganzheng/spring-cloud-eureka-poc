# spring-cloud-eureka-poc

主要是为了测试一下Eureka的HA机制。

针对这个帖子反映的问题：[Eureka doesn't replicate its registry info to all servers](https://stackoverflow.com/questions/39118722/eureka-doesnt-replicate-its-registry-info-to-all-servers)，做了一个实际测试。

三个Eureka Server: peer1 -> peer2, peer2 -> peer3, peer3 -> peer1
一个Eureka Client: client -> peer1

测试结果：

client 在 peer1 和 peer2上有注册信息，但是在peer3上没有。如下图所示：

![eureka-server-peer1-info](https://github.com/arganzheng/spring-cloud-eureka-poc/raw/master/eureka-server-peer1-info.jpeg)
![eureka-server-peer1-info](https://github.com/arganzheng/spring-cloud-eureka-poc/raw/master/eureka-server-peer2-info.jpeg)
![eureka-server-peer1-info](https://github.com/arganzheng/spring-cloud-eureka-poc/raw/master/eureka-server-peer3-info.jpeg)

**结论**

Eureka并不是一个一致性的注册中心，只是一个简单的数据同步来保证高可用，但是并没有集群的概念。


### 参考文章

1. [Service Registration and Discovery](https://spring.io/guides/gs/service-registration-and-discovery/)
2. [Microservice Registration and Discovery with Spring Cloud and Netflix's Eureka](https://spring.io/blog/2015/01/20/microservice-registration-and-discovery-with-spring-cloud-and-netflix-s-eureka)





