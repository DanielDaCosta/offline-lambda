# offline-lambda
Testing an AWS Lambda offline.

Repo for testing a lambda function locally.

# Details
- event.json: file that contains the lambda *event*
- lambda/: lambda code

# Usage
Command for invoking lambda.Starting the Docker container corresponds to an AWS Lambda cold start.
```
docker-compose run lambda lambda.handler.lambda_handler "$(cat event.json)"
```

Command for keeping the container of our Lambda function running: you can make several consecutive calls quickly without waiting for the “cold start” times.
```
docker-compose run -e DOCKER_LAMBDA_STAY_OPEN=1 lambda lambda.handler.lambda_handler "$(cat event.json)"
```

# Acknowledgments
Special Thanks for Vittorio Nardone for the medium post:
- https://levelup.gitconnected.com/aws-lambda-offline-development-with-docker-6a8cf8b186e7
- https://hub.docker.com/r/lambci/lambda/
