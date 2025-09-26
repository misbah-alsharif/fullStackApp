FROM maven:3.9.6-eclipse-temurin-17 AS build
WORKDIR /app
COPY ./demo/demo/pom.xml /app/pom.xml    
COPY ./demo/demo/src /app/src            
RUN mvn clean package -DskipTests

# مرحلة التشغيل
FROM eclipse-temurin:17-jdk-alpine
WORKDIR /app
COPY --from=build /app/target/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","app.jar"]
