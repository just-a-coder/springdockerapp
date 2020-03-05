# demoSpringApp
 This is a Sample SpringBoot App for Testing
 
 # Creating Sample SpringBoot Project
     
  Step 1: Open Spring Initializr
     https://start.spring.io/
     Create a Java Project using Gradle.
     One file will be downloaded.
     Open That File in your IDE.
     
  Step 2: 
     In resources Add
         a) application.yml
             Setup spring.profiles.active: local
         b) application-local.yml
     In Gradle Add:
             For Web Project:
         	implementation 'org.springframework.boot:spring-boot-starter-web'
         	For Lombok
         	compileOnly 'org.projectlombok:lombok:1.18.12'
         	annotationProcessor 'org.projectlombok:lombok:1.18.12'
     
  # Run Project either from Run IDE
  #   ./gradlew clean build
  java -jar build/libs/jarname-snapshot.jar
     * Project will~~~~~~~~~~~~~~~~~~~~ Start *
     
     --------------------------------------------------
  # Containerize It
  So let’s go ahead and create a Dockerfile in our Spring Boot project:
     
  Dockerfile:
     
  FROM openjdk:8-jdk-alpine
  ARG JAR_FILE=target/*.jar
  COPY ${JAR_FILE} app.jar
  ENTRYPOINT ["java","-jar","/app.jar"]
     
  Execute:
  docker build --build-arg JAR_FILE=build/libs/*.jar -t springio/spring-boot-docker .
  # Download Will Begin
     
  To Run The Docker Image
  docker run -p 8090:8080 -t springio/demo .
  Spring Boot apps run on port 8080 inside the container by default and we mapped
  that to the same port on the host using "-p" on the command line.
