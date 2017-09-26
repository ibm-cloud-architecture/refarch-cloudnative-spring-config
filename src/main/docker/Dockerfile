FROM openjdk:8-alpine
VOLUME /tmp

ENV GIT_USER root
ENV GIT_EMAIL root@localhost

RUN mkdir -p /app/spring-config/repo
RUN apk --no-cache update \
  && apk add -y git

RUN cd /app/spring-config/repo \
  && git init \
  && touch application.properties \
  && git config user.email "${GIT_EMAIL}" \
  && git config user.name "${GIT_USER}" \
  && git add . \
  && git commit -m "Baseline commit"
VOLUME /app/spring-config/repo

ADD app.jar app.jar
RUN sh -c 'touch /app.jar'
EXPOSE 8888
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/app.jar"]
