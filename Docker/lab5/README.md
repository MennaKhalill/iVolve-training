# Multi-Stage Build for a Java Spring Boot App

This lab demonstrates how to use a multi-stage Docker build to create a smaller, optimized Docker image for a Java Spring Boot application. The workflow includes cloning the source code, writing a multi-stage Dockerfile, building the Docker image, running a container, testing the app, and stopping/removing the container.

---

## Step 1: Clone the Repository

Clone the source code from GitHub:

```bash
git clone https://github.com/Ibrahim-Adel15/Docker-1.git
cd Docker-1
```
![Repository Cloned](https://github.com/MennaKhalill/iVolve-training/blob/main/Docker/lab5/screenshots/clone.png)

## Step 2: Write a Multi-Stage Dockerfile

Create a Dockerfile in the project folder:
```bash
vim Dockerfile
```
```dockerfile
# Stage 1: Build the application using Maven
FROM maven:3-eclipse-temurin-17-alpine AS build
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn package 

# Stage 2: Create a runtime image
FROM eclipse-temurin:17-jdk-alpine
WORKDIR /app
COPY --from=build /app/target/demo-0.0.1-SNAPSHOT.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
```

## Step 3: Build the Docker Image

Build the Docker image named app3:

```bash
docker build -t app3 .
```
![Build](https://github.com/MennaKhalill/iVolve-training/blob/main/Docker/lab5/screenshots/build_image.png)

## Step 4: Run the Container

Run a container named container3 from the image app3 and map port 8080:

```bash
docker container run -d --name container3 -p 8080:8080 app3
```
![Run](https://github.com/MennaKhalill/iVolve-training/blob/main/Docker/lab5/screenshots/run_container.png)

---

## Step 5: Test the Application

Use curl to check if the application is running:

```bash
curl http://localhost:8080
```
![Test](https://github.com/MennaKhalill/iVolve-training/blob/main/Docker/lab5/screenshots/test.png)

---

## Step 6: Stop and Remove the Container

Stop and remove the running container:

```bash
docker stop container3
docker rm container3
```
![Stop](https://github.com/MennaKhalill/iVolve-training/blob/main/Docker/lab5/screenshots/stop.png)

---

## Summary

This project demonstrates:

- Cloning a Spring Boot repository
- Writing a multi-stage Dockerfile
- Building the application with Maven in a build stage
- Creating a lightweight runtime stage with only Java
- Building a Docker image (app3) optimized for size
- Running the Spring Boot app in a container
- Testing the app using curl
- Stopping and removing the container
