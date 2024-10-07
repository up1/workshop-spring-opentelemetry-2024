


## Order service with Java and Spring Boot
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