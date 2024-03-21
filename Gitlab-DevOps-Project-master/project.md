# GitLab Practice Project: Run - Build imgae - Push - Deploy

This repository is a GitLab practice project based on the fork of [benc-uk/python-demoapp](https://github.com/benc-uk/python-demoapp.git). The goal is to demonstrate setting up a CI/CD pipeline using GitLab CI/CD features.

## Steps Taken:

### Step 1: Test Execution with Makefile

I started by running the following command to check how the tests for this specific project can be executed using the Makefile:

```bash
make test
```
<img width="738" alt="step 1" src="https://github.com/nishathmhd/DevOps-CICD-Projects/assets/117710744/e0172e12-3efd-4554-a3c1-5f93472b7205">


### Step 2: Pipeline Configuration

I created a pipeline configuration file named `.gitlab-ci.yml`. This file defines the stages, jobs, and steps for the CI/CD process.

<img width="444" alt="crteated yaml file" src="https://github.com/nishathmhd/DevOps-CICD-Projects/assets/117710744/355631e2-d854-4322-9e05-20666bf34634">


### Step 3: Running Tests

In GitLab, I created jobs in the pipeline to run tests, build the Docker image, and deploy the application. Here's an overview of how the tests were run:

<img width="427" alt="gitlab jobs" src="https://github.com/nishathmhd/DevOps-CICD-Projects/assets/117710744/53d438f4-af2a-46ec-81aa-665ab9046cdb">


### Step 4: Building and Pushing Docker Image

I set up Docker Hub to push the created Docker image. This involved configuring authentication and pushing the image to the Docker Hub registry.


<img width="738" alt="Docker hub" src="https://github.com/nishathmhd/DevOps-CICD-Projects/assets/117710744/a51dc0f2-ea8b-4f78-9622-b1f70bb6f3e5">

### Step 5: Writing Pipeline Configuration

I defined the pipeline configuration in `.gitlab-ci.yml`, specifying the necessary steps to build, test, and deploy the application. This included defining stages such as `test`, `build`, and `deploy`, along with corresponding job configurations.

<img width="394" alt="Write Pipleline Confifration" src="https://github.com/nishathmhd/DevOps-CICD-Projects/assets/117710744/9d75b0b3-660c-4134-912f-9d467e73c0c6">


### My whole pipeline code and explained

```bash
variables:
  IMAGE_NAME: nishathmhd/gitlab-devops
  IMAGE_TAG: python-app-1.0
```
This section defines variables that can be used throughout the pipeline.
IMAGE_NAME represents the name of the Docker image.
IMAGE_TAG represents the tag of the Docker image.

```bash
stages:
  - test
  - build
```
This section defines the stages of the pipeline.
The pipeline has two stages: test and build.
Jobs defined in the test stage will run first, followed by jobs in the build stage.

```bash
run_test:
  stage: test
  image: python:3.12-slim
  before_script:
    - apt-get update && apt-get install -y make git 
  script:
    - make test
```
This section defines a job named run_test, which belongs to the test stage.
It specifies that the job will run in a Docker image based on Python 3.12 (specifically, the slim version).
The before_script section specifies commands that will be executed before the script section.
In this case, it updates the package index and installs make and git.
The script section specifies the actual commands to be executed.
Here, it runs the make test command, which presumably runs tests for the project.

```bash
build_image:
  stage: build
  image: docker:26.0.0-rc2-cli
  services:
    - docker:26.0.0-rc2-dind 
  before_script:
    - docker login -u "$DOCKER_USER" -p "$DOCKER_PASS"
  script: 
    - docker build -t "$IMAGE_NAME:$IMAGE_TAG" .
    - docker push "$IMAGE_NAME:$IMAGE_TAG" 
```
This section defines a job named build_image, which belongs to the build stage.
It specifies that the job will run in a Docker image with Docker CLI version 26.0.0-rc2.
The services section specifies additional Docker services required by the job.
Here, it includes the Docker daemon (docker:26.0.0-rc2-dind) to enable Docker-in-Docker functionality.
The before_script section specifies commands to be executed before the script section.
Here, it logs into Docker Hub using provided credentials (DOCKER_USER and DOCKER_PASS are expected to be set as environment variables).
The script section specifies the commands to be executed.
First, it builds the Docker image using the Dockerfile in the current directory and tags it with the specified image name and tag.
Then, it pushes the built Docker image to Docker Hub.
