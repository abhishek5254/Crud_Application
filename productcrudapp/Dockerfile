# Use a Maven base image for building the project
FROM maven:3.8.5-openjdk-17 AS builder

# Set the working directory in the container
WORKDIR /app

# Copy the Maven project files
COPY pom.xml .
COPY src ./src

# Build the project
RUN mvn clean package

# Use a base image with Java to run the application
FROM openjdk:17-jdk-alpine

# Set the working directory in the container
WORKDIR /app

# Copy the jar file from the builder stage
COPY --from=builder /app/target/your-app.jar /app/your-app.jar

# Specify the command to run your application
CMD ["java", "-jar", "your-app.jar"]

# Expose the port your app runs on
EXPOSE 8080
