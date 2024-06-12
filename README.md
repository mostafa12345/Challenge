# Overview

This repository contains a PHP Laravel API and a Nuxt.js Client. The setup includes Dockerfiles for both the API and Client, and a Docker Compose file to orchestrate the services. The API connects to a MySQL database, and an Nginx web server acts as a proxy, forwarding requests to the Client. Additionally, a self-signed certificate is generated for the Nginx web server to listen on port 443.
   
**Dockerfiles**
**PHP Laravel API Dockerfile**

The Dockerfile for the PHP Laravel API is located in the api directory.

**Nuxt.js Client Dockerfile**

The Dockerfile for the Nuxt.js Client is located in the client directory.

**Docker Compose File**

The docker-compose.yml file at the root directory orchestrates the services, including MySQL, the Laravel API, the Nuxt.js Client, and Nginx.

**Self-Signed Certificate**

A self-signed SSL certificate is generated for the Nginx server to make it listen on port 443.
Steps to Run the Project
Prerequisites

**Ensure you have the following installed:**

    Docker
    Docker Compose
    OpenSSL (for generating the self-signed certificate)

**Step 1: Clone the Repository**

**Clone the repository to your local machine:**

    git clone https://github.com/your-repository.git
    cd your-repository


**Step 2: Build and Run the Containers**

    Navigate to the root directory and run:
    docker-compose up --build -d 
    docker-compose up -d 

**This command will:**

    Build the Docker images for the API and Client
    Start the containers for MySQL, the Laravel API, the Nuxt.js Client, and Nginx

**Step 4: Access the Application**

    The API is accessible at http://localhost:8000
    The Client is accessible at http://localhost
    The Nginx server with the self-signed SSL certificate is accessible at https://localhost

**CI/CD using GitHub Actions**

The project includes a GitHub Actions workflow to automate the process of building and pushing Docker images to Docker Hub.
Set Up GitHub Actions

    Ensure you have a Docker Hub account.
    Add your Docker Hub credentials to the GitHub repository secrets:
        DOCKER_USERNAME: Your Docker Hub username
        DOCKER_PASSWORD: Your Docker Hub password

The workflow will automatically run on each push to the main branch, building and pushing the Docker images for the API and Client to Docker Hub.
