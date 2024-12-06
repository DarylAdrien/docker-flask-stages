# Docker Flask Application - Single Stage & Multi Stage

This repository demonstrates the usage of Docker for a Flask web application. The project contains two separate folders:

- **single-stage-dockerfile**: A simple Flask application containerized using a single-stage Dockerfile.
- **multi-stage-dockerfile**: A Flask application containerized using a multi-stage Dockerfile for optimized image size and separation of build and runtime environments.

The main goal of this repository is to understand how Docker works with Flask applications and to compare the benefits of single-stage vs. multi-stage Dockerfiles.


## Single-Stage Dockerfile

The **single-stage Dockerfile** is a straightforward Docker configuration that includes all dependencies (including build tools) in a single image. This method is simple but may result in larger images since everything (including development dependencies) is bundled into the final image.

### Steps to build and run the Flask app using Single-Stage Dockerfile

1. Navigate to the `single-stage-dockerfile` folder:
   
   ```bash
   
   cd single-stage-dockerfile
   
3. Build the Docker image:
   
   ```bash

   docker build -t flask-single-stage .

5. Run the container:
   
   ```bash

   docker run -p 5000:5000 flask-single-stage

Visit the Flask app in your browser: Open http://localhost:5000.




## Multi-Stage Dockerfile

The multi-stage Dockerfile is designed to optimize the image by separating the build environment from the runtime environment. It uses one image to build the application and another to run it. This reduces the size of the final image by excluding development dependencies and build tools.
Steps to build and run the Flask app using Multi-Stage Dockerfile


### Steps to build and run the Flask app using Single-Stage Dockerfile


1. Navigate to the multi-stage-dockerfile folder:

   ```bash

    cd multi-stage-dockerfile

2. Build the Docker image:

   ```bash

   docker build -t flask-multi-stage .

3. Run the container:

   ```bash

   docker run -p 5000:5000 flask-multi-stage


Visit the Flask app in your browser: Open http://localhost:5000.






