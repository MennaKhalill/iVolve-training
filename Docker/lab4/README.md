# Run Java Spring Boot App in a Container

This lab demonstrates how to containerize a Java Spring Boot application using Docker. The workflow includes cloning the source code, building the application, writing a Dockerfile, building a Docker image, running a container, testing the application, and stopping/removing the container.

---

## Step 1: Clone the Repository

Clone the application from GitHub:

```bash
git clone https://github.com/Ibrahim-Adel15/Docker-1.git
cd Docker-1
```
![Repository Cloned](https://github.com/MennaKhalill/iVolve-training/blob/main/Docker/lab4/screenshots/clone.png)

## Step 2: Build the Application (Locally)

Make sure you have Maven installed and run:

```bash
mvn package
```
![Build](https://github.com/MennaKhalill/iVolve-training/blob/main/Docker/lab4/screenshots/package.png)

## Step 3: Write the Dockerfile

Create a Dockerfile in the project folder:
```bash
vim Dockerfile
```
```dockerfile
FROM eclipse-temurin:17-jdk-alpine
WORKDIR /app
COPY target/demo-0.0.1-SNAPSHOT.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","app.jar"]
```
## Step 4: Build the Docker Image

Build the Docker image named app2:

```bash
docker build -t app2 .
```
![Build](https://github.com/MennaKhalill/iVolve-training/blob/main/Docker/lab4/screenshots/build.png)

## Step 5: Run the Container

Run a container named container2 from the image app2 and map port 8080:

```bash
docker container run -d --name container2 -p 8080:8080 app2
```
![Run](https://github.com/MennaKhalill/iVolve-training/blob/main/Docker/lab4/screenshots/container.png)

---

## Step 6: Test the Application

Use curl to check if the application is running:

```bash
curl http://localhost:8080
```
![Test](https://github.com/MennaKhalill/iVolve-training/blob/main/Docker/lab4/screenshots/test.png)

---

## Step 7: Stop and Remove the Container

Stop and remove the running container:

```bash
docker stop container2
docker rm container2
```
![Stop](https://github.com/MennaKhalill/iVolve-training/blob/main/Docker/lab4/screenshots/stop.png)

---

## Summary

This project demonstrates:
- Cloning a Spring Boot application repository
- Building the application using Maven
- Writing a Dockerfile for a Java 17-based container
- Building a Docker image
- Running the Spring Boot app inside a container
- Testing the app using curl
- Stopping and removing the container
