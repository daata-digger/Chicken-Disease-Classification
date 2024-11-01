# 🐔 Chicken Disease Classification Project

This repository contains the end-to-end code for the **Chicken Disease Classification** project, designed to classify images of chickens with various diseases. The project is deployed using AWS and Azure, with continuous integration and continuous deployment (CI/CD) facilitated by GitHub Actions.

---

## 📋 Table of Contents

- Project Overview
- Setup and Installation
- Data Version Control (DVC)
- Deployment
  - AWS Deployment with GitHub Actions
  - Azure Deployment with GitHub Actions
- Acknowledgments

---

## 📝 Project Overview

The Chicken Disease Classification project leverages deep learning techniques to identify and classify diseases in chickens based on image data. The project includes the following features:
- Data preprocessing and model training pipeline
- Continuous integration and deployment workflows using GitHub Actions
- Deployment on AWS EC2 and Azure Web App, using Docker for containerization

---

## 🛠️ Setup and Installation

Follow these steps to set up and run the project locally:

### STEPS:

1. **Clone the repository**:
   ```bash
   git clone https://github.com/entbappy/Chicken-Disease-Classification--Project.git
   cd Chicken-Disease-Classification--Project
2. **Create a Conda environment:**:
   ```bash
	conda create -n cnncls python=3.8 -y
	conda activate cnncls
3. **Install the required dependencies:**:
   ```bash
	pip install -r requirements.txt
4. **Run the application:**:
   ```bash
	python app.py
Now, open your browser and navigate to http://localhost:PORT to access the application.

# 📦 Data Version Control (DVC)
The project uses DVC for version control of datasets and model artifacts.

1. **Initialize DVC:**:
   ```bash
	dvc init
1. **Initialize DVC:**:
   ```bash
	dvc repro
1. **Initialize DVC:**:
   ```bash
	dvc dag
# 🚀 Deployment
The deployment for this project can be done on AWS or Azure, using GitHub Actions for CI/CD automation.

# **AWS Deployment with GitHub Actions**
To deploy this project on AWS, follow these steps:

Login to AWS Console and create an IAM user with the following permissions:

EC2 Access: for managing virtual machines.
ECR Access: for storing Docker images.
IAM Policies:

AmazonEC2ContainerRegistryFullAccess
AmazonEC2FullAccess
Create an ECR Repository to store Docker images.

Save the repository URI, e.g., 566373416292.dkr.ecr.us-east-1.amazonaws.com/chicken.
Launch an EC2 Instance (Ubuntu) and install Docker:

1. **Launch an EC2 Instance (Ubuntu) and install Docker:**
   ```bash
   sudo apt-get update -y
   sudo apt-get upgrade -y
   curl -fsSL https://get.docker.com -o get-docker.sh
   sudo sh get-docker.sh
   sudo usermod -aG docker ubuntu
   newgrp docker
Configure EC2 as a Self-Hosted GitHub Runner:

Go to Settings > Actions > Runners > New self-hosted runner in your GitHub repository and follow the instructions for Ubuntu.
Setup GitHub Secrets:

Add the following secrets in your GitHub repository settings:
AWS_ACCESS_KEY_ID: Your AWS access key.
AWS_SECRET_ACCESS_KEY: Your AWS secret access key.
AWS_REGION: us-east-1
AWS_ECR_LOGIN_URI: e.g., 566373416292.dkr.ecr.us-east-1.amazonaws.com
ECR_REPOSITORY_NAME: chicken
Deployment Workflow:

The GitHub Actions workflow will:
Build a Docker image of the source code.
Push the Docker image to ECR.
Launch an EC2 instance and pull the image from ECR.
Run the Docker container on EC2.

# **Azure Deployment with GitHub Actions**
To deploy this project on Azure, follow these steps:

1. **Save Azure Password:**
   ```bash
	s3cEZKH5yytiVnJ3h+eI3qhhzf9q1vNwEi6+q+WGdd+ACRCZ7JD6
1. **Initialize DVC:**:
   ```bash
	docker build -t chickenapp.azurecr.io/chicken:latest .
	docker login chickenapp.azurecr.io
	docker push chickenapp.azurecr.io/chicken:latest
**Deployment Workflow:**

The GitHub Actions workflow will:
Build the Docker image of the source code.
Push the Docker image to Azure Container Registry.
Launch the Web App Server on Azure.
Pull the Docker image from the container registry to the Web App server and run it.
