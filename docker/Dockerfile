FROM java:8
VOLUME /tmp

ENV GIT_USER root
ENV GIT_EMAIL root@localhost

RUN mkdir -p /app/spring-config/repo
RUN apt-get update && apt-get install -y git
RUN cd /app/spring-config/repo && git init && touch application.properties && git config user.email "${GIT_EMAIL}" && git config user.name "${GIT_USER}" && git add . && git commit -m "Baseline commit"
VOLUME /app/spring-config/repo

ADD app.jar app.jar
RUN bash -c 'touch /app.jar'
EXPOSE 8080
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/app.jar"]
