# Demo with Spring Boot 3.3.4
* Database => PostgreSQL
* [OpenTelemetry](https://opentelemetry.io/)
* Logging
  * [Loki](https://grafana.com/oss/loki/)
* Distributed tracing
  * [Jaeger tracing](https://www.jaegertracing.io/)
* Application metric
  * [Prometheus](https://prometheus.io/)
  

## 1. Order service with Java and Spring Boot
Build image
```
$docker compose build order_service
```

Start container
```
$docker compose up -d order_service
```

Status of containers
```
$docker compose ps                 
NAME                        IMAGE               COMMAND                  SERVICE         CREATED          STATUS                    PORTS
otel-demo-order_service-1   order_service:1.0   "java -jar api.jar"      order_service   21 seconds ago   Up 9 seconds              0.0.0.0:8080->8080/tcp
postgres                    postgres:17         "docker-entrypoint.s…"   postgres        21 seconds ago   Up 20 seconds (healthy)   5432/tcp
```

List of APIs
* http://localhost:8080/orders/1
* http://localhost:8080/orders/2

## 2. Observability of services
* Otel collector
  * Logging with loki
  *
```
$docker compose up -d collector
$docker compose ps
```

### Open grafana server = http://localhost:3000
* Login
    * username=admin
    * password=admin
* Go to menu explore to query login data
    * Filter by job = order-service

### Open Jaeger server = http://localhost:16686
* Filter by service = order-service
