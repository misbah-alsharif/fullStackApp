FROM maven:3.9.6-eclipse-temurin-17 AS build
WORKDIR /app

# نسخ ملفات pom.xml و src من المسار الصحيح
COPY . . 

RUN mvn clean package -DskipTests

# مرحلة التشغيل
FROM eclipse-temurin:17-jdk-alpine
WORKDIR /app
COPY --from=build /app/target/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","app.jar"]
