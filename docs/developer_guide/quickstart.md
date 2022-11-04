# Quickstart
## Requirements
Make sure that you have JDK>=17, Gradle, Docker, docker-compose, node>=18.12.0 with npm, and Python>=3.10 installed.

## Set Up Your Development Environment
1. Clone the projects for the [frontend](https://github.com/MathGrass/mathgrass-frontend) and the [backend and evaluator](https://github.com/MathGrass/mathgrass-server) 
1. Start the dependencies of the API and the evaluator(PostGres & RabbitMQ) either manually or the provided [docker compose project](https://github.com/MathGrass/mathgrass-server/blob/develop/api/docker/mathgrass-backend-infrastructure.yaml) via ```docker-compose -f mathgrass-backend-infrastructure.yaml up -d``` in the folder ```mathgrass-server/api/docker```
1. Import the gradle project under ```mathgrass-server/api``` into your favorite Java IDE and run the application (entrypoint: ```MathgrassServerApplication.java```) with the Spring profile ```demodata``` (or not, if no demodata should be present).
1. Import the React project under ```mathgrass-frontend``` into your favorite TypeScript IDE and run ```npm install && npm run start```
1. You can check whether the project has build correctly by checking the following paths on localhost:
    - [Swagger UI (http://localhost:8080/swagger-ui/)](http://localhost:8080/swagger-ui/)
    - [Frontend (http://localhost:3000)](http://localhost:3000)
