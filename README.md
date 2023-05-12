# Notes

## Spring Boot 3 Distributed Tracing With Micrometer and Zipkin Configuration 

### Maven pom.xml

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

### application.yml

```yaml
logging:
  pattern:
    level: '%5p [${spring.application.name:},%X{traceId:-},%X{spanId:-}]'

management:
  tracing:
    sampling:
      probability: 1.0
```

### Zipkin

```console
docker run -d -p 9411:9411 openzipkin/zipkin
```
## Python Virtual Environment Setup

```console
pip install virtualenv
cd project_directory
virtualenv venv
source ./venv/bin/activate
pip install python-dotenv paramiko
pip freeze > requirements.txt

pip install -r requirements.txt
```

## Load Balancer Algorithms

- **Round Robin**: distributed across group of servers sequentially
- **Least Connections**: sent to server with fewest active connections
- **Least Time**: sent to server with fastest response time and fewest active connections
- **Hash**: distribution based on a key (e.g. IP address or Request URL)
- **IP Hash**: distribution based on the IP address of the client
- **Random with Two Choices**: randomly pick 2 servers and select the one by least connections
