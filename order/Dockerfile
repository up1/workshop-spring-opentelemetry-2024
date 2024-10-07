FROM maven:3.9.9-eclipse-temurin-23 AS step01
WORKDIR /xyz
COPY . .
RUN --mount=type=cache,target=/root/.m2 mvn clean package -DskipTests

FROM eclipse-temurin:23-jre-alpine
WORKDIR /build
COPY --from=step01 /xyz/target/api.jar .
EXPOSE 8080
ENTRYPOINT [ "java" ]
CMD ["-jar", "api.jar"]