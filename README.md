# calculator-api

This API is a simple calculator web service implemented using Java. It caches the results of its computations, with endpoints in a format similar to the following:

- /add/{a}/{b}/{c}
- /subtract/{a}/{b}/{c}
- /multiply/{a}/{b}/{c}
- /divide/{a}/{b}

For the operations of addition, subtraction, and multiplication, the calculator endpoints should support an input of up to three numbers in the same call.

Each endpoint should support the GET method, and it should return the result in JSON format. If there is more than one call for the same operation on the same numbers, then the result should be returned from the cache rather than being recomputed. 

## Deploying to Heroku

docker login --username=<email> password=$(heroku auth:token) registry.heroku.com
docker build -t registry.heroku.com/calculator-java-maven-service/web:$VERSION --build-arg value=$VERSION .
docker build -t registry.heroku.com/calculator-java-maven-service/web:latest --build-arg value=$VERSION .
docker push registry.heroku.com/calculator-java-maven-service/web:latest
heroku container:login
heroku container:rm web -a calculator-java-maven-service
heroku container:release web -a calculator-java-maven-service
