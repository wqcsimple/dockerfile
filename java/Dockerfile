FROM java:8u91

COPY UnlimitedJCEPolicy/local_policy.jar /usr/lib/jvm/java-8-openjdk-amd64/jre/lib/security/local_policy.jar
COPY UnlimitedJCEPolicy/US_export_policy.jar /usr/lib/jvm/java-8-openjdk-amd64/jre/lib/security/US_export_policy.jar

ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/opt/java/app.jar","--spring.config.location=/opt/java/application.properties"]
