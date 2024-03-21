# GitLab Practice Project: Python Demo App

This repository is a GitLab practice project based on the fork of [benc-uk/python-demoapp](https://github.com/benc-uk/python-demoapp.git). The goal is to demonstrate setting up a CI/CD pipeline using GitLab CI/CD features.

## Steps Taken:

### Step 1: Test Execution with Makefile

I started by running the following command to check how the tests for this specific project can be executed using the Makefile:

```bash
make test
```
<img width="738" alt="step 1" src="https://github.com/nishathmhd/Gitlab-DevOps-Project/assets/117710744/a0d8f37a-648f-4584-8bb4-91648b9d33b7">


### Step 2: Pipeline Configuration

I created a pipeline configuration file named `.gitlab-ci.yml`. This file defines the stages, jobs, and steps for the CI/CD process.

<img width="444" alt="crteated yaml file" src="https://github.com/nishathmhd/Gitlab-DevOps-Project/assets/117710744/6c6c2ddf-6e7f-4e70-82bb-14aea7f8903f">


### Step 3: Running Tests

In GitLab, I created jobs in the pipeline to run tests, build the Docker image, and deploy the application. Here's an overview of how the tests were run:

<img width="427" alt="gitlab jobs" src="https://github.com/nishathmhd/Gitlab-DevOps-Project/assets/117710744/ffa55f93-65c2-415e-b2e3-3b6ea4ec3c4b">


### Step 4: Building and Pushing Docker Image

I set up Docker Hub to push the created Docker image. This involved configuring authentication and pushing the image to the Docker Hub registry.

<img width="738" alt="Docker hub" src="https://github.com/nishathmhd/Gitlab-DevOps-Project/assets/117710744/cd95b538-2082-40d9-95f2-eebbdd1fb39a">


### Step 5: Writing Pipeline Configuration

I defined the pipeline configuration in `.gitlab-ci.yml`, specifying the necessary steps to build, test, and deploy the application. This included defining stages such as `test`, `build`, and `deploy`, along with corresponding job configurations.

<img width="394" alt="Write Pipleline Confifration" src="https://github.com/nishathmhd/Gitlab-DevOps-Project/assets/117710744/99f0a12f-a454-47b2-b3e9-5c97e43a42a7">

