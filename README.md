# JHipster Registry

[![Build Status][travis-image]][travis-url]  [![Docker Pulls](https://img.shields.io/docker/pulls/jhipster/jhipster-registry.svg)](https://hub.docker.com/r/jhipster/jhipster-registry/)

This is the [JHipster](https://www.jhipster.tech/) registry service, based on [Spring Cloud Netflix](http://cloud.spring.io/spring-cloud-netflix/), [Eureka](https://github.com/Netflix/eureka) and [Spring Cloud Config](http://cloud.spring.io/spring-cloud-config/).

Full documentation is available on the [JHipster documentation for microservices](https://www.jhipster.tech/microservices-architecture).

## Deploy to Heroku

Click this button to deploy your own instance of the registry:

[![Deploy to Heroku](https://www.herokucdn.com/deploy/button.png)](https://heroku.com/deploy)

There are a few limitations when deploying to Heroku.

* The registry will only work with [native configuration](https://www.jhipster.tech/jhipster-registry/#spring-cloud-config) (and not Git config).
* The registry service cannot be scaled up to multiple dynos to provide redundancy. You must deploy multiple applications (i.e. click the button more than once). This is because Eureka requires distinct URLs to synchronize in-memory state between instances.

## Running locally

To run the cloned repository;
* For development run `./mvnw -Pdev,webpack` to just start in development or run `./mvnw` and run `yarn && yarn start` for hot reload of client side code.
* For production profile run `./mvnw -Pprod`

[travis-image]: https://travis-ci.org/jhipster/jhipster-registry.svg?branch=master
[travis-url]: https://travis-ci.org/jhipster/jhipster-registry

## Running locally on docker (ubuntu 18.04)

1. Install docker
2. git clone https://github.com/pervezcse/jhipster-registry.git
3. Uncooment the following part in pom file:
```
<executions>
    <execution>
        <id>default</coid>
        <goals>
            <goal>build</goal>
            <goal>push</goal>
        </goals>
    </execution>
</executions>
```
4. This `sudo ./mvnw package -Pprod -DskipTests` command will build and push docker image in local docker repo.
5. To check the image run `sudo docker image ls`
6. Run command `sudo docker run -dit --restart unless-stopped -p 8761:8761 jhipster-registry:latest`
7. Go to the link `http://localhost:8761`

## Helpful commands for docker:
sudo docker container ps -a
sudo docker container stats
sudo docker container stop <CONTAINER ID>

sudo docker rm $(sudo docker ps -a -q)
sudo docker rmi $(sudo docker images -q)
sudo docker kill $(sudo docker ps -q)


