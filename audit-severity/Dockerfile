FROM openjdk:16
EXPOSE 8300
ADD target/audit-severity.jar audit-severity.jar
ENTRYPOINT ["java","-jar","/audit-severity.jar"]