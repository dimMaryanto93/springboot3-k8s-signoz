ARG JDK_VERSION=17-alpine
FROM --platform=amd64 eclipse-temurin:${JDK_VERSION}
LABEL maintener="Dimas Maryanto <software.dimas_m@icloud.com>"

ENV SERVER_PORT=8080

# installing os dependencies
RUN apk add wget curl

# setup application
WORKDIR /usr/share/applications

ARG JAR_FILE="springweb-1.0.0-release.jar"
COPY target/${JAR_FILE} spring-boot.jar
RUN wget https://github.com/open-telemetry/opentelemetry-java-instrumentation/releases/latest/download/opentelemetry-javaagent.jar

ENTRYPOINT ["java", "-jar", "-Djava.security.egd=file:/dev/./urandom", "spring-boot.jar"]

CMD ["--server.port=${SERVER_PORT}"]
EXPOSE ${SERVER_PORT}/tcp