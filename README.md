# Casaba Java SDK

## Getting Started

#### Environment

Casaba Java SDK runs under JDK 8.

#### Fork this project

This project contains all required dependencies to run Casaba SEA API server.

#### Update configurations

update `src/resources/application.yml` with sdk credentials you applied from
Casaba SEA platform.

#### Up and running

```bash
./gradlew bootRun
```


## Docs Explorer

After start api server, you can found the doc under http://localhost:8080/graphiql


## Extend the API

#### GraphQL API

Casaba SEA SDK using `graphql-braid` to talking with Casaba SEA backend server
and it is easy to extend by adding hooks and plugins.

#### REST API

Casaba SEA SDK is a standard Spring Boot project, you can follow Spring Boot guide
to extend it.

## Packaging and deployment


#### Spring Boot Package

Spring Boot provides a Gradle plugin to support it's own packing structure
and produces a runnable application.

#### Spring Profiles

You can also use Spring profiles to manage different and to deploy
a specific environment.

And you can using following command to run a uat environment application:

```
java -jar java-sdk-example.jar -Dspring.profiles.active=uat
```

#### Packaging with Docker

...

#### Kubernetes Deployment

...