# Udacity AWS Cloud DevOps Engineer - Project 03: Operationalizing a Co-working Space Service

## Project Overview

**Coworking Space Service**

The Coworking Space Service consists of APIs enabling users to request one-time tokens and administrators to authorize access to a coworking space. Following a microservice pattern, the APIs are organized into distinct services deployable and manageable independently.

As a DevOps engineer in this project, you collaborate with a team constructing an API for business analysts. The provided application functions as expected, and your role involves building a pipeline to deploy it to Kubernetes.

## Workspace Environment Requirements

You'll need these tools to compete this project:

- **Python Environment** - run Python 3.6+ applications and install Python dependencies via pip
- **Docker CLI** - build and run Docker images locally
- **kubectl** - run commands against a Kubernetes cluster
- **helm** - apply Helm Charts to a Kubernetes cluster
- **GitHub** - pull and clone code

## Remote Resource Requirements

This project utilizes Amazon Web Services (AWS). The AWS resources you'll need to use for the project include:

- **AWS CLI**
- **AWS CodeBuild** - build Docker images remotely
- **AWS ECR** - host Docker images
- **Kubernetes Environment with AWS EKS** - run applications in k8s
- **AWS CloudWatch** - monitor activity and logs in EKS

## How to run 🚀

### Initial Steps

1. **Clone Project Code**:

   ```
   git clone https://github.com/ivanurra/cd12355-microservices-aws-kubernetes-project
   ```

2. **Database Initialization**:

- Build the provided database Dockerfile located in the 'db' directory. Supply arguments to establish the database connections.

3. **App configuration**:

- Construct the application's Dockerfile, incorporating runtime variables to configure **DB_USERNAME** and **DB_PASSWORD**. Ensure these credentials are consistent with the ones specified in step 2.

### Project Deployment Workflow

#### 1. AWS CodeBuild Pipeline Activation:

The deployment process starts with the execution of the `buildspec.yml` file in AWS CodeBuild. This step involves processing and packaging the application. Replace all environment variables with your own.

#### 2. Docker Image Repository:

AWS CodeBuild then pushes the newly built Docker image to an Amazon ECR repository.

#### 3. Kubernetes Deployment:

Utilize the Image ARN to update the `analytics-api.yml` deployment file. This file, along with the database configuration files, orchestrates the deployment of the service on Kubernetes.

#### 4. Service Availability:

The associated pods within the analytics service are initiated, bringing the application online and operational.

#### 5. AWS CloudWatch:

Kubernetes clusters created with EKS are configured to integrate with CloudWatch Container Insights by default. This integration captures essential metrics, including CPU, memory, disk usage, and network traffic details. Additionally, container diagnostic data is also captured.

