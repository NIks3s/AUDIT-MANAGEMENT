FROM openjdk:16
EXPOSE 8250
ADD target/audit-benchmark.jar audit-benchmark.jar
ENTRYPOINT ["java","-jar","/audit-benchmark.jar"]