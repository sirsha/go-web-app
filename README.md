# DevOpsify the go web application

The main goal of this project is to implement DevOps practices in the Go web application. The project is a simple website written in Golang. It uses the net/http package to serve HTTP requests.

![Website](static/images/golang-website.png)

## DevOps practices include the following:

- Creating Dockerfile (Multi-stage build)
- Containerization
- Continuous Integration (CI)
- Continuous Deployment (CD)

### In this demo, we will see how to deploy an Go web application on EKS cluster, utilizing GitHub Actions for continuous integration, ArgoCD for continuous deployment.
#


### <mark>Project Deployment Flow:</mark>



<img src="https://github.com/sirsha/go-web-app/blob/main/Golang.drawio.png" />


#
## Tech stack used in this project:
- GitHub (Code)
- Github Actions (CI)
- Docker (Containerization)
- ArgoCD (CD)
- AWS EKS (Kubernetes)
- Helm 


## Running the server

To run the server, execute the following command:

```bash
go run main.go
```

The server will start on port 8080. You can access it by navigating to `http://localhost:8080/courses` in your web browser.

### How pipeline will look after deployment:
- <b>CI pipeline to build, unit test, static code analysis and push</b>

![image](https://github.com/sirsha/wanderlust/blob/devops/images/Screenshot%202025-07-25%20205322.png)

- <b>ArgoCD application for deployment on EKS</b>

![image](https://github.com/sirsha/wanderlust/blob/devops/images/diagram-export-7-25-2025-8_58_10-PM.png)

# Steps to implement the Project 
## Creating  Dockerfile (Multi-stage build) and containerization
We’ll create the Docker image using a **multi-stage build**, a Docker feature that enables multiple build phases within a single Dockerfile. This approach helps minimize the final image size and enhances security by excluding unnecessary files and packages.
picture

  #
- <b id="Argo">We will use Docker to containerize the Go web application. </b>
  - <b>Commands to build the Docker container</b>
  ```bash
  docker build -t <your-docker-username>/go-web-app .
  ```
  - <b>Command to run the Docker container:</b>
  ```bash
  docker run -p 8080:8080 <your-docker-username>/go-web-app
  ```
  - <b>Command to push the Docker container to Docker Hub</b>
  ```bash
  docker push <your-docker-username>/go-web-app
  ```

## INGRESS CONTROLLER CONFIGURATION
In this project, we’re using the **NGINX Ingress Controller**, a Go-based program developed by LB. It continuously monitors Kubernetes ingress resources and provisions load balancers according to the specified ingress configurations.

## CONTINIOUS INTEGRATION
We will use GitHub Actions to implement CI for the Go web application. GitHub Actions is a feature of GitHub that allows you to automate workflows, such as building, testing, and deploying code.

The GitHub Actions workflow will run the following steps:

Checkout the code from the repository
Build the Docker image
Run the Docker container
Run tests

## CONTINIOUS DEPLOYMENT
We will use Argo CD to implement CD for the Go web application. Argo CD is a declarative, GitOps continuous delivery tool for Kubernetes. It allows you to deploy applications to Kubernetes clusters using Git as the source of truth.

The Argo CD application will deploy the Go web application to a Kubernetes cluster. The application will be automatically synced with the Git repository, ensuring that the application is always up to date.

## CONCLUSION
This process has not only strengthened my skills in Kubernetes, containerization, CI/CD, GitOps but also reinforced the importance of continuous learning and collaboration in building scalable, secure systems.

**NEXT UP:**  I’m planning to dive deeper into GitOps workflows, advanced Kubernetes security (OPA Gatekeeper, Kyverno) and also integrate Monitoring like Prometheu and Grafana.





