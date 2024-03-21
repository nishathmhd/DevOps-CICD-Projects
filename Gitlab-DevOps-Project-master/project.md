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

