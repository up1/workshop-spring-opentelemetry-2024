FROM maven:3.9.9-eclipse-temurin-23 AS step01
WORKDIR /xyz
COPY . .
RUN --mount=type=cache,target=/root/.m2 mvn clean package -DskipTests

FROM eclipse-temurin:23-jre-alpine
ARG version=2.8.0
WORKDIR /build
COPY --from=step01 /xyz/target/api.jar .
ADD --chmod=644 https://github.com/open-telemetry/opentelemetry-java-instrumentation/releases/download/v$version/opentelemetry-javaagent.jar /usr/src/app/opentelemetry-javaagent.jar
ENV JAVA_TOOL_OPTIONS=-javaagent:/usr/src/app/opentelemetry-javaagent.jar
EXPOSE 8080
ENTRYPOINT [ "java" ]
CMD ["-jar", "api.jar"]