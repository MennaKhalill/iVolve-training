# Run Java Spring Boot App in a Container


This project demonstrates how to containerize a Java Spring Boot application using Docker. The steps include cloning the source code, writing a Dockerfile, building the Docker image, running the container, testing the application, and stopping/removing the container.

---

## Step 1: Clone the Repository

Clone the source code from GitHub:

```bash
git clone https://github.com/Ibrahim-Adel15/Docker-1.git
cd Docker-1
```
![Repository Cloned](https://github.com/MennaKhalill/iVolve-training/blob/main/Docker/lab3/screenshots/clone.png)

## Step 2: Write the Dockerfile

Create a Dockerfile in the project folder:
```bash
vim Dockerfile
```
```dockerfile
FROM maven:3-eclipse-temurin-17-alpine
WORKDIR /app
COPY . .
RUN mvn package
EXPOSE 8080
CMD ["java", "-jar", "target/demo-0.0.1-SNAPSHOT.jar"]
```

## Step 3: Build the Docker Image

Build the Docker image named app1:

```bash
docker build -t app1 .
```
![Build](https://github.com/MennaKhalill/iVolve-training/blob/main/Docker/lab3/screenshots/build_image.png)

## Step 4: Run the Container

Run a container named container1 from the image app1 and map port 8080:

```bash
docker container run -d --name container1 -p 8080:8080 app1
```
![Run](https://github.com/MennaKhalill/iVolve-training/blob/main/Docker/lab3/screenshots/run_container.png)

---

## Step 5: Step 5: Test the Application

Use curl to check if the application is running:

```bash
curl http://localhost:8080
```
![Test](https://github.com/MennaKhalill/iVolve-training/blob/main/Docker/lab3/screenshots/run_container.png)

---

## Step 6: Stop and Remove the Container

Stop and remove the running container:

```bash
docker stop container1
docker rm container1
```
![Stop](https://github.com/MennaKhalill/iVolve-training/blob/main/Docker/lab3/screenshots/stop_rm.png)

---

## Summary

This project demonstrates:

- Cloning a Spring Boot application repository
- Writing a Dockerfile for a Maven-based Java app
- Building a Docker image
- Running the app inside a container
- Testing the application using curl
- Stopping and removing the container
