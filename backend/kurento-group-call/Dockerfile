FROM maven:3.8.7-eclipse-temurin-17 AS build

WORKDIR /app

COPY . .

RUN mvn clean package spring-boot:repackage -DskipTests

FROM eclipse-temurin:17-jdk-jammy
WORKDIR /app

COPY --from=build /app/target/kurento-group-call-6.18.0-exec.jar app.jar

RUN chmod +x app.jar

CMD ["java", "-jar", "app.jar"]
