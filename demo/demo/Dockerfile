# ===== Build stage =====
FROM maven:3.9.6-eclipse-temurin-17 AS build
WORKDIR /app

# تعديل المسارات عندك
COPY /demo/pom.xml ./pom.xml
COPY /demo/src ./src

# بناء المشروع بدون اختبارات
RUN mvn clean package -DskipTests

# ===== Run stage =====
FROM eclipse-temurin:17-jdk-alpine
WORKDIR /app

# نسخ الملف الناتج من مرحلة البناء
COPY --from=build /app/target/*.jar app.jar

# فتح البورت
EXPOSE 8080

# تشغيل التطبيق
ENTRYPOINT ["java", "-jar", "app.jar"]
