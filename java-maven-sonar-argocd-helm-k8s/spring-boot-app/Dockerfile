# You can change this base image to anything else
# But make sure to use the correct version of Java
FROM adoptopenjdk/openjdk11:alpine-jre

# Simply the artifact path
ARG artifact=target/spring-boot-web.jar

# Install Maven (Alpine way)
RUN apk update && \
    apk add --no-cache maven && \
    mvn -version

# Install Maven (Following is the apt way)    
#RUN apt-get update && \
    #apt-get install -y maven && \
    #mvn -version

WORKDIR /opt/app

COPY ${artifact} app.jar

# This should not be changed
ENTRYPOINT ["java","-jar","app.jar"]

#===Follwoing is the Best practice=======================
# Build stage
#FROM maven:3.9.9-eclipse-temurin-11 AS build
#WORKDIR /build
#COPY . .
#RUN mvn clean package -DskipTests

# Runtime stage
#FROM adoptopenjdk/openjdk11:alpine-jre
#WORKDIR /opt/app
#COPY --from=build /build/target/*.jar app.jar
#ENTRYPOINT ["java","-jar","app.jar"]
