# Notes

## Java 

### Spring Boot 3 Distributed Tracing With Micrometer and Zipkin Configuration 

#### Maven pom.xml

```xml
<dependency>
    <groupId>io.micrometer</groupId>
    <artifactId>micrometer-observation</artifactId>
</dependency>
<dependency>
    <groupId>io.micrometer</groupId>
    <artifactId>micrometer-tracing-bridge-brave</artifactId>
</dependency>
<dependency>
    <groupId>io.zipkin.reporter2</groupId>
    <artifactId>zipkin-reporter-brave</artifactId>
</dependency>
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
<dependency>
    <groupId>io.github.openfeign</groupId>
    <artifactId>feign-micrometer</artifactId>
</dependency>
```

#### application.yml

```yaml
logging:
  pattern:
    level: '%5p [${spring.application.name:},%X{traceId:-},%X{spanId:-}]'

management:
  tracing:
    sampling:
      probability: 1.0
```

#### Zipkin

```console
docker run -d -p 9411:9411 openzipkin/zipkin
```

#### Kafka

```console
bin/zookeeper-server-start.sh config/zookeeper.properties
bin/kafka-server-start.sh config/server.properties
bin/kafka-console-consumer.sh --topic amigoscode --from-beginning --bootstrap-server localhost:9092
```
## AWS

#### AWS CLI

```console
aws secretsmanager get-secret-value --secret-id test/full-stack/postgres

docker run --rm -it postgres psql -U amigoscode -h host -d ebdb
```

## Python

### Python Virtual Environment Setup

#### Install virtual environment and dependencies

```console
pip install virtualenv
cd project_directory
virtualenv venv
source ./venv/bin/activate
pip install python-dotenv paramiko
pip freeze > requirements.txt
```
#### Re-install dependencies for virtual environment

```console
cd project_directory
source ./venv/bin/activate
pip install -r requirements.txt
```
## Glossories

### Load Balancer Algorithms

- **Round Robin**: distributed across group of servers sequentially
- **Least Connections**: sent to server with fewest active connections
- **Least Time**: sent to server with fastest response time and fewest active connections
- **Hash**: distribution based on a key (e.g. IP address or Request URL)
- **IP Hash**: distribution based on the IP address of the client
- **Random with Two Choices**: randomly pick 2 servers and select the one by least connections

### Kubernetes (K8S)

#### Master Node 
- Control Plane
  - API Server: all communication go through
  - Scheduler: assign pods to nodes
  - Cluster Store: etcd - configuration and state of cluster
  - Controller Manager
    - Watch loop
    - Each controller watches API changes and keep desired state=current state
  - Cloud Controller Manager
    - interact with underlying cloude provider

## External Resources

### Spring Boot
[Online Spring Boot Banner Generator (with FIGlet Fonts)](https://devops.datenkollektiv.de/banner.txt/index.html)

### Kubernetes
[Kubernetes NodePort vs LoadBalancer vs Ingress? When should I use what?](https://medium.com/google-cloud/kubernetes-nodeport-vs-loadbalancer-vs-ingress-when-should-i-use-what-922f010849e0)
