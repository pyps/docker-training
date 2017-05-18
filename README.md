## Docker-training
A quick Docker Training

Thest the image with:
```docker-compose up -d && docker-compose logs -f otto_exercise```

```
otto_exercise_1  | Replacing unittest ottonova
otto_exercise_1  | .
otto_exercise_1  | ----------------------------------------------------------------------
otto_exercise_1  | Ran 1 test in 0.026s
otto_exercise_1  |
otto_exercise_1  | OK
otto_exercise_1  |  * Running on http://0.0.0.0:5000/ (Press CTRL+C to quit)
otto_exercise_1  | 24.134.21.245 - - [18/May/2017 19:27:25] "GET / HTTP/1.1" 200 -
otto_exercise_1  | Replacing unittest ottonova
otto_exercise_1  | .
otto_exercise_1  | ----------------------------------------------------------------------
otto_exercise_1  | Ran 1 test in 0.019s
otto_exercise_1  |
otto_exercise_1  | OK
otto_exercise_1  |  * Running on http://0.0.0.0:5000/ (Press CTRL+C to quit)
```

1.) Found the Docker training webapp in Docker Hub. (https://hub.docker.com/r/training/webapp/)

```docker pull training/webapp:latest```


2.) Basic docker-compose is at https://github.com/pyps/docker-training/tree/8e074ea2345c78b4a5bd2d7d463220e844faa2f7


3.) Added mongo database to the service list: https://github.com/pyps/docker-training/tree/84440ebb13bb54bed4e7b940705c890fe1cc533b


4.) Add unittest execution at startup. https://github.com/pyps/docker-training/blob/12f78d06c6a1114ec9400c7c12f780965c6d71b8/docker-compose.yml
Overwrite the startup command with a shell piped command.


5.) Return message from env variable. Adjust unittest. https://github.com/pyps/docker-training/tree/23ad17e741693fcf3a8fbd2fb59fb95e11a65464
Replace the unittest inline with the given Env variable.
**Warning** Container content is altered during startup. Bad practice.


### Deploy with docker tools:

Simple:
Deploy the docker-compose file to the target host. (Docker, docker-compose and connection to Registry required)
Start the services with ```docker-compose up -d```

Or:
Set your docker socket connection to target host (Docker and registry connection required) and start services from your local Docker client.


### Deploy in a non-Docker environment

Base: Trusted OS image
Middleware: python installation via configuration management
Service: MongoDB installation via configuration management
Service: Deploy a fixed and tested version of the application. Create a python virtual environment during deployment for the needed dependencies. ("pyvenv env")
         Start the application with the newly created venv

         /bin/bash -c "source env/bin/activate; python app.py"
         via Deployment tooling
Ops: Create startup systemd unit for startup behaviour and log management

-----

This docker image is a good example that you should split configuration and code:
* Unittest should be executed during Image build and not during startup.
* Configuration Input should not be executed directly.

Tested with docker-compose binary version 1.13.0/1.8.0 and docker-compose file version 2.0/3
