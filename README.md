Docker Compose Assignment
Problem Statement

In this assignment, you will expand your Docker skills by setting up multiple containers and enabling them to communicate with each other using Docker Compose. You will be provided with the Python code for two services: a Flask web application and a Redis service. Your task is to:

    Initialize a new repository.
    Create the correct directory structure.
    Write the Dockerfiles for both services.
    Write the docker-compose.yml file to define and run the multi-container application.
    Ensure the containers can communicate with each other.

Instructions
Step 1: Set Up the Repository

    Initialize a new Git repository.
    Navigate to the root directory of the repository.

Step 2: Create the Directory Structure

Create the following directory structure:

docker-compose-basics/
├── web/
│   ├── app.py
│   ├── requirements.txt
│   └── Dockerfile
├── redis/
│   └── Dockerfile
└── docker-compose.yml

Step 3: Flask Web Application

Inside the web/ directory, create a file named app.py with the following content:

from flask import Flask
from redis import Redis

app = Flask(__name__)
redis = Redis(host='redis', port=6379)

@app.route('/')
def hello_world():
    count = redis.incr('hits')
    return f'Hello World! This page has been visited {count} times.'

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)

Create a requirements.txt file in the web/ directory with the following content:

flask
redis

Step 4: Redis Dockerfile

Inside the redis/ directory, create a Dockerfile with the following content:

# Use the official Redis image from the Docker Hub as the base image
FROM redis:alpine

Step 5: Flask Dockerfile

Inside the web/ directory, create a Dockerfile with the following comments. Your task is to fill in the correct Docker instructions:

# Use the official Python image from the Docker Hub as the base image
#

# Set the working directory in the container to /app
#

# Copy the current directory contents into the container at /app
#

# Install any needed packages specified in requirements.txt
#

# Make port 5000 available to the world outside this container
#

# Define environment variable
#

# Run app.py when the container launches
#

Step 6: Write the docker-compose.yml File

In the root directory, create a docker-compose.yml file with the following comments. Your task is to fill in the correct Docker Compose configurations:

version: '3'

services:
  web:
    # Build the web service using the Dockerfile in the web directory
    #
    ports:
      - "5000:5000"
    depends_on:
      - redis
  redis:
    # Build the redis service using the Dockerfile in the redis directory
    #
    ports:
      - "6379:6379"

Step 7: Build and Run the Containers

Build and start the Docker Compose application:

docker-compose up --build

Open your browser and navigate to http://localhost:5000 to see the Flask application, which should display the number of visits to the page.
