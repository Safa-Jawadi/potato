---
sidebar_position: 0
---

# DevOps Course
The workflow of this course is that we will learn DevOps culture and it's tools while creating a project and we will start step by step in case of a basic knowledge is needed in IT we will explain it so everyone are in the same level7

## Module 1: Introduction to DevOps
- Understanding the Origins of DevOps:
    the DevOps story: Carrefour France (Told by Walid Dridi SRE at Carrefour France)
- Problems DevOps Aims to Solve
- DevOps Principles and Values: Collaboration and communication requirements to ensure smooth product delivery to production(Client)

## Module 2: Functioning of DevOps Engineer in Real Life
- Tools that we work with on daily basis:
  * Version Control : Git & Git Platforms: Bitbucket Github Gitlab
  * CI/CD tools: Jenkins, SonarQube, Nexus
  * Configuration Management tools: Ansible
  * Containerization: Docker
  * Orchestration: Kubernetes
  * and More advanced stuff...
- CI/CD Deployment Methods (Blue/Green, Canary, Rolling)
- Illustration of a CI/CD Pipeline

## Module 3: Understand the Application
- Prepare the environment for the Application Locally
- Exploring Environment Variables and Configuration of the application
- Run the application 
- Debugging and Troubleshooting if any problem occurs (typically you can ask the developer team for help)

## Module 4: Version Control with Git and GitHub
- Git Basics (Commits, Branches, Merging): the Demo will be pushing their application to Github Repository using Git Commands
- Introduction to GitFlow Workflow and versioning
- Collaborative Work with GitHub ( Create Github Organization and manage the students repository)
- Branch Management and Pull Requests (to simulate Company workflow when making changes to main branch)
- Demo:
```bash
    Create a "repository" (project) with a git hosting tool (like Bitbucket)
  
    Copy (or clone) the repository to your local machine
  
    Add a file to your local repo and
  
    "commit" (save) the changes
  
    "Push" your changes to your main branch
  
    Make a change to your file with a git hosting tool and commit
  
    "Pull" the changes to your local machine
  
    Create a "branch" (version), make a change, commit the change
  
    Open a "pull request" (propose changes to the main branch)
  
    "Merge" your branch to the main branch
```
## Module 5: Linux and Networking Essentials 
DevOps will always contain Developing basics and Operation Basics that's why managing linux servers is a fundemntal part of DevOps 
- Introduction to Linux (basic commands + basic services (SSHD etc....) + bash scripting)
- Networking Fundamentals:
  Protocols(TCP, IP, ...)
  networking configurations
  Setting up a network on Linux
  troubleshooting networking issues
- Web Servers (Nginx, Apache) what is it and it's use case in deployment

# Module 6: Docker and Containerization

- What is Containerization?
- Docker vs. Virtualization
- Importance of Docker in DevOps
- Docker CLI: works with container (basic commands docker pull/run/stop/rm/ps/logs/exec)
- Understanding Docker Networking and Volumes
- Building new Docker Image for our application with Dockerfiles

The Project: Dockerize our aplication (3-tier) using Docker file
- What is Docker Compose and how it can help us create multiple docker container? and how it can help us in DevOps 

Project: Setup our CI/CD tools using docker

## Module 7: CI/CD Automation
- What is CI/CD and the objective of automate the manual steps from building testing and deploying
  Continuous Integration
  Continuous Testing
  Continuous Deployment
  Continuous Delivery
- Building, Testing, and Deploying with Docker
- Container Registries like Nexus and Dockerhub 

Project: Create a CI Pipeline to automate building testing and storing application artifacts 

## Module 8: Configuration Management with Ansible
- Introduction to Ansible
- Basics of Ansible Playbooks, hosts, variables, AnsibleFacts and more (configuration dynamic inventory roles....)
- Setting Up a Web Server with Ansible 
- Create ansible playbook to deploy our application

Project: Create ansible playbooks to configure the VPC or cloud Server and deploy our application and finally integrate ansible with our Pipeline to ensure continuous Deployment


## Module 9: Kubernetes in Practice
- Core Concepts (control plane, ETCD, Controllers, Kubelete, Container Runtime Engine CRI )
- Kuberentes ressources (Pods, Replicaset Deployments, Services)
- Scaling and Load Balancing with Kubernetes
- Integrating Kubernetes into CI/CD Pipeline
