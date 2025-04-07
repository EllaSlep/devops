FROM maven:3.8.6-eclipse-temurin-17-alpine AS build
WORKDIR /app

COPY pom.xml .
COPY mvnw .
RUN mvn dependency:go-offline -B

COPY src ./src
RUN mvn package -DskipTests

FROM eclipse-temurin:17-jre-alpine
WORKDIR /app

RUN addgroup -S spring && adduser -S spring -G spring \
    && chown -R spring:spring /app
USER spring

COPY --from=build --chown=spring:spring /app/target/*.jar app.jar

RUN rm -rf /var/cache/apk/*

ENV SPRING_PROFILES_ACTIVE=default

EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]