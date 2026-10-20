
FROM maven:3.9.9-eclipse-temurin-21-alpine AS build

COPY . /app
WORKDIR /app

RUN mvn clean install -DskipTests

FROM tomcat:10-jdk21


RUN rm -rf /usr/local/tomcat/webapps/*

COPY --from=build /app/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]
