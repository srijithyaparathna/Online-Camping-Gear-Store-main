# Final Project: Containerization and CI/CD Automation

This repository contains the code and configuration files for my final project, which involves containerizing an application and automating the deployment process using CI/CD tools.

## Project Overview

The project consists of the following steps:

1. **Research and Containerization**
   - Search for and understand how to containerize the application based on the chosen technology stack.
   - Example: Containerize a MERN Stack Application using Docker.
![image](https://github.com/srijithyaparathna/Online-Camping-Gear-Store-main/assets/125755221/43a0cc7e-de9c-4a98-8715-a16a1542fef9)

2. **Manual Docker Containerization**
   - Create Dockerfiles, build Docker images, and run containers manually.

3. **CI/CD Automation**
   - Automate the containerization and deployment process using CI/CD tools such as Jenkins, Ansible, or Terraform.
   - The automation process should include:
     1. Retrieving code from the Git repository.
     2. Building Docker containers.
     3. Running the application within Docker containers.

## Project Structure

```plaintext
.
├── Dockerfile
├── Jenkinsfile
├── README.md
├── app
│   ├── Dockerfile
│   ├── src
│   ├── package.json
│   └── ...
├── scripts
│   ├── build.sh
│   ├── deploy.sh
│   └── ...
└── terraform
    ├── main.tf
    └── ...
