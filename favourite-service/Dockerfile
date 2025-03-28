FROM maven:3.9.6-eclipse-temurin-17 AS builder
WORKDIR /home/app

# Copy source code and build the JAR inside the container
COPY . .
RUN /bin/sh -c /bin/sh -c mvn clean package -DskipTests

# Use a lighter JDK image for running the app
FROM openjdk:17
WORKDIR /home/app

# Copy the built JAR from the builder stage
COPY --from=builder /home/app/target/favourite-service-0.0.1-SNAPSHOT.jar favourite-service.jar

EXPOSE 8888
ENTRYPOINT ["java", "-jar", "favourite-service.jar"]
