# syntax=docker/dockerfile:experimental
FROM eclipse-temurin:8-jdk-alpine as build
WORKDIR /workspace/app

COPY mvnw .
COPY .mvn .mvn
COPY pom.xml .
COPY src src

RUN --mount=type=cache,target=/root/.m2 ./mvnw install -DskipTests

FROM eclipse-temurin:8-jdk-alpine
VOLUME /tmp
ARG EXTRACTED=/workspace/app/target/*.jar
COPY --from=build ${EXTRACTED} app.jar
ENTRYPOINT ["java","-jar","/app.jar"]