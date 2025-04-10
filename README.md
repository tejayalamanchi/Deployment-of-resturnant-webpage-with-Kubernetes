# Restaurant Website Deployment with Docker and Kubernetes

## Overview

This project demonstrates how to deploy a static restaurant website using **Docker** and **Kubernetes**. The website is containerized using Docker and then orchestrated and scaled using Kubernetes to ensure high availability, fault tolerance, and ease of access. The service is exposed through Kubernetes' `NodePort` to allow external traffic to access the website.

## Technologies Used

- **Docker**: Used to containerize the static website, ensuring portability and consistency across various environments.
- **Kubernetes**: Used for orchestrating the containers, managing deployments, services, and scaling the application.
- **HTML**: Basic static content used to create a restaurant website.
- **NodePort Service**: Used for exposing the website externally via a specific port.

## Project Features

- **Containerization**: The static website is packaged into a Docker container, enabling a consistent and reproducible environment.
- **Kubernetes Deployment**: The website is deployed in a Kubernetes cluster, which automatically manages scaling and fault tolerance.
- **External Access**: The website is made accessible to external users by exposing it through Kubernetes NodePort service.
- **Scalability**: The website can easily scale by adjusting the number of replicas in the Kubernetes deployment.
  

### 1. **Dockerfile**
   - Contains instructions for creating the Docker image of the static website.
  
### 2. **deployment.yaml**
   - Contains the Kubernetes deployment configuration to manage the website’s pod and ensure high availability.

### 3. **service.yaml**
   - Contains the Kubernetes service configuration to expose the website externally using `NodePort`.

### 4. **index.html**
   - The main HTML file for the static restaurant website.

## Steps to Run Locally

1. **Clone the repository**:

    ```bash
    git clone https://github.com/teja2610/Deployment-of-resturnant-webpage-with-Kubernetes.git
    cd restaurant-website-deployment
    ```

2. **Build the Docker image**:

    ```bash
    docker build -t project-site .
    ```

3. **Push the Docker image to Docker Hub**:

    ```bash
    docker tag project-site teja2610/project-site
    docker push teja2610/project-site
    ```

4. **Create the Kubernetes Deployment and Service**:

    Apply the deployment and service YAML files to your Kubernetes cluster:

    ```bash
    kubectl apply -f deployment.yaml
    kubectl apply -f service.yaml
    ```

5. **Check if the pods and services are running**:

    ```bash
    kubectl get pods
    kubectl get svc
    ```

6. **Access the Website**:

   After the service is successfully exposed, access the static website by navigating to the external IP of the node and the assigned port (`30081` in this case):

    ```bash
    http://<Node-IP>:30081
    ```

## How It Works

1. **Dockerization**: 
   The static restaurant website is packaged into a Docker container, which includes all necessary dependencies to run the website.

2. **Kubernetes Deployment**: 
   The Docker container is deployed on Kubernetes using a `Deployment` resource. Kubernetes manages the lifecycle of the pod, ensuring that it is running and scaled as needed.

3. **Kubernetes Service**: 
   A `NodePort` service is created to expose the website externally, allowing users to access it through a specific port on any node of the cluster.

4. **Scaling**: 
   Kubernetes makes it easy to scale the application by increasing the number of pod replicas, which helps handle more traffic and ensure high availability.

## Future Enhancements

- **CI/CD Integration**: Automate the process of building Docker images, pushing them to Docker Hub, and deploying the application using CI/CD tools like Jenkins or GitHub Actions.
- **TLS/SSL Encryption**: Secure the website using HTTPS by integrating an Ingress Controller with TLS termination.
- **Monitoring and Logging**: Implement monitoring and logging for better visibility into the application’s performance and health.

## Conclusion

This project provided hands-on experience with Docker and Kubernetes, demonstrating the power of containerization and orchestration for modern web applications. We successfully deployed a static website in a Kubernetes cluster, ensuring scalability, availability, and reliability.


