# docker-training
A qick Docker Training

1.) Found the docker training webapp in Docker HUB.
[https://hub.docker.com/r/training/webapp/]

    docker pull training/webapp:latest

2.) Basic docker-compose is at 8e074ea2345c78b4a5bd2d7d463220e844faa2f7

3.) Added mongo databse to the app service <commit>


4.) Add unittest startup <commit>

5.) Return message from env variable. Adjust unittest. <commit>



### Deploy with docker tools:

Simple:
Deploy the docker-compose file to the target host. (Docker, docker-compose and connection to Registry required)
Start the services with "docker-compose up -d"

Set your docker socket connection to target host and start services from your local Docker client.


### Deploy in a non-Docker environment

Base: Trusted OS image
Middleware: python installation via configuration management
Service: MongoDB installation via configuration management
Service: Deploy a fixed and tested version of the application. Create a python virtual environment during deployment for the needed dependencies. ("pyvenv env")
         Start the application with the newly created venv

         /bin/bash -c "source env/bin/activate; python app.py"
         via Deployment tooling
Ops: Create startup systemd unit for startup behaviour and log management

