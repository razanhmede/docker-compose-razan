In this repository,the docker-compose-basics folder contains 2 other folders and a docker-compose.yml file: 
- in the web folder there is an app.py python code, the requirements text file and the docker file.
- in the redis folder, there is a docker file.
>For the flask web application :
-In the app.py file, the flask web application is initialized and Redis service running on host "redis" corresponding the docker-container defined in the docker-compose.yml file on port 6379.
An app route '/' was defined and it increments a redis counter 'hits' and returns the number of visits.
-In the requirements text file the python dependencies flask and redis libraries were listed.
-In the docker file for flask application :
The python image alpine was used as the base image among other images such and buster and slim.
The current directory contents we copied into the container and port 5000 was exposed to flask application
>In the docker file for Redis: the base image for redis was specified using also alpine.
>The docker-compose.yml file defines two services: Flask application and redis.
Redis service maps port 6379 on the host to port 6379 in the container.
The flask service depends on the redis service to run before.

The docker compose sets up the communication between the web service and the redis service and the two can communicate using their hostnames.
Output: when a request is made to the flask's app route '/', it increments the redis counter and returns the number of visits along side "Hello world!" using http://localhost:5000.

