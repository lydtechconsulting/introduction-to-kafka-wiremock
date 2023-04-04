# udemy-kafka-beginner-wiremock

This project contains a standalone wiremock implementation for use with the udemy-kafka-beginner
project. It represents a third-party stock service which is called by the despatch service of the udemy-kafka-beginner project
The API call is in the following format :

GET /api/stock?item=myItem

The wiremock is primed to return the following responses:
400 - if the item ends with the string "_400" e.g. GET /api/stock?item=myItem_400
500 - if the item ends with the string "_500"
502 - if the item ends with the string "_502" fail the first call then succeed. This allows for retry testing
200 - for all other items



To run the wiremock service type the following:

First download the wiremock standalone jar file using the instructions found here:
https://wiremock.org/docs/running-standalone/

And copy it to this project directory: 

The run wiremock using the following command (replace wiremock-jre8-standalone-2.35.0.jar with the name of the downloaded jar file) 

java -jar wiremock-jre8-standalone-2.35.0.jar --port 9001

This will start the service on port 9001, which is what the dispatch service in the udemy-kafka-beginner 
project will attempt to call in on