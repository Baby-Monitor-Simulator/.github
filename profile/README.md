# Baby Monitor Simulator
This is the public repository containing all source code and documentation related to the Baby Monitor Simulator.

# Required MatLab extensions
The following extensions are required to run the simulation `FMPmodel.m` (version 1, not 2):
* Symbolic math toolbox
* Statistics and machine learning toolbox
* Signal processing toolbox

# Setups
## General development Setup
1. Download the setup-microservices.ps1 file
2. Open Powershell with administrator privileges (windows key + x)
3. Run the script line by line:
   3.1 Set-ExecutionPolicy RemoteSigned
   3.2 .\setup-microservices.ps1

### Working with Docker Compose

Once initial setup is complete, you can begin developing with Docker Compose. Here’s a step-by-step guide on how to do this:

1. Navigate to the Project Directory:
   Open a terminal (PowerShell or Command Prompt) and navigate to the `microservices-dev` folder:
   
   cd C:\Users\<YourUsername>\Desktop\microservices-dev

2. Build the application using .\mvnw clean packages -DskipTests if this doesn't work go to Maven > lifecycle > package. The Jar generated in your Target folder will be used by the docker container to hot-reload while working on code.

3. Start the Docker Desktop application

4. Build the first Dockerfile locally. Run the docker command:  docker-compose -f docker-compose.dev.yml build 
(if you are running into issues, you can rebuild the image after troubleshooting and using  docker-compose -f docker-compose.dev.yml build --no-cache this makes the docker image download all dependencies again rather than what has already been downloaded previously)

5. Start the Services: Use the following command to start the microservices defined in the docker-compose.dev.yml file:
   docker-compose -f docker-compose.dev.yml up

     The -f flag tells docker-compose to use a specific file. In this case, it's a file solely used for development. You might ask why: This setup of docker points the docker container to the application we're   
     running locally while still using all the dependencies and java version created in the image. This gives us the advantage of steady dependency management but allows us to develop locally and easily share 
     with others.

   This command will build the images (if not already built) and start the containers for each microservice.

6. Accessing services: Each service can be accessed at the port defined in the docker-compose.yml file

7. Hot Reloading: Changes made to the source code in the gateway-api or identity-service folders will automatically be reflected in the running containers due to the volume mounts defined in the docker-compose.yml file. This allows for a smoother development experience without needing to rebuild the containers.

### Docker Compose commands:

Shutting down the services can be done by either pressing CTRL + C in the terminal where docker-compose up is running. Alternatively you can use docker-compose down

Viewing the logs can be done using docker-compose logs or docker-compose logs  <service_name>

Running Migrations or Initialization Scripts: If your services require database migrations or any initialization scripts, ensure that these are integrated within the services’ Dockerfiles or handled through entrypoint scripts. You may need to execute these after starting the containers or define specific commands in the docker-compose.yml.

Check status of running containers: docker ps

To access a running containers shell: docker exec -it <container_id_or_name> /bin/sh

# Deployment

- [Frontend](https://github.com/Baby-Monitor-Simulator/frontend-webui?tab=readme-ov-file#project-setup)
- [Backend](https://github.com/Baby-Monitor-Simulator/backend-matlab/tree/master?tab=readme-ov-file#setup)

# Static code analysis tool
> https://sonarcloud.io

Use provided _GitHub_ account.

# Documentation
> https://github.com/Baby-Monitor-Simulator/docs

# Wiki
> https://github.com/Baby-Monitor-Simulator/wiki/wiki

# FAQ
> https://github.com/Baby-Monitor-Simulator/wiki/wiki/FAQ

# Support
> Contact - babymonitor@fontys.nl

