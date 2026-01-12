# Building and Packaging Java Applications with Gradle

This folder demonstrates a complete Gradle workflow for building and running a Java application. The steps include installing Gradle, running unit tests, building the application, and running it.

---

## Step 1: Clone the Source Code

Clone the source code from GitHub:

```bash
git clone  https://github.com/Ibrahim-Adel15/build1.git
```
![Repository Cloned](https://github.com/MennaKhalill/iVolve-training/blob/main/Build_Tools/lab1/screenshots/clone.png)

## Step 2: Run Unit Test

Execute the unit tests for the project:

```bash
cd build1
gradle test
```
![unit_test](https://github.com/MennaKhalill/iVolve-training/blob/main/Build_Tools/lab1/screenshots/test.png)

## Step 3: Build the Project

Build the project into a JAR file:

```bash
gradle build
```
![Build](https://github.com/MennaKhalill/iVolve-training/blob/main/Build_Tools/lab1/screenshots/build.png)

## Step 4: Run the Application

Run the packaged Java application using:

```bash
java -jar build/libs/ivolve-app.jar

```
![Run](https://github.com/MennaKhalill/iVolve-training/blob/main/Build_Tools/lab1/screenshots/run.png)
---

## Summary

The full workflow of using Gradle in this project:

Clone the repository from GitHub.
Run unit tests to verify functionality.
Build the JAR artifact with Gradle.
Run the application using the Java runtime.
