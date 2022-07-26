FROM openjdk:16
EXPOSE 8100
ADD target/audit-authorization.jar audit-authorization.jar
ENTRYPOINT ["java","-jar","/audit-authorization.jar"]