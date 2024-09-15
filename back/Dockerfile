FROM ubuntu:latest AS buid
RUN apt-get update
RUN apt-get install openjdk-17-jdk -y
COPY . .
RUN ./gradlew bootJar --no-daemon

FROM openjdk:17-jdk-slim
EXPOSE 3000
COPY --from=buid /buid/libs/back-0.0.1-SNAPSHOT app.bootJar

ENTRYPOINT ["java","-jar","app.jar"]