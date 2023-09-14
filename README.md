# Introduction to Kafka with Spring Boot - Standalone Wiremock

This repository contains the code to support the [Introduction to Kafka with Spring Boot](https://github.com/lydtechconsulting/introduction-to-kafka-wiremock.git) online course, for the standalone Wiremock portion of the course.

The associated repository for the Dispatch Service can be found here:  [Dispatch Service Repository](https://github.com/lydtechconsulting/introduction-to-kafka-with-spring-boot)

This project contains a standalone Wiremock implementation that represents a third-party Stock Service which is called by the Dispatch Service and used to trigger retry scenarios.

## Introduction to Kafka with Spring Boot Course Wiki
Plenty of useful information about your Introduction to Kafka with Spring Boot course can be found in the [Wiki](https://github.com/lydtechconsulting/introduction-to-kafka-with-spring-boot/wiki).

## Stock Service API

The API call is in the following format:

```
GET /api/stock?item=myItem
```

The wiremock is primed to return the following responses:

- `400` - if the item ends with the string `_400` e.g. `GET /api/stock?item=myItem_400`
- `500` - if the item ends with the string `_500`
- `502` - if the item ends with the string `_502` fail the first call then succeed. This allows for retry testing.
- `200` - for all other items

## Run the Wiremock

First download the Wiremock standalone jar file using the instructions found here:
https://wiremock.org/docs/running-standalone/

Copy the jar to this project directory.

Run the Wiremock by using the following command (replacing wiremock-jre8-standalone-2.35.0.jar with the name of the downloaded jar file): 
```
java -jar wiremock-jre8-standalone-2.35.0.jar --port 9001
```

The service will start on port `9001`, which is where the Dispatch Service will attempt to call it.

## Connect with the team at Lydtech Consulting
* Visit us at [lydtechconsulting.com](https://www.lydtechconsulting.com/)
* Visit our [LinkedIn](https://www.linkedin.com/company/lydtech-consulting) page
