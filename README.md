# Final Project

The application I am working with is a simple Tic Tac Toe Game web-based
application that i got from [Tic-Tac-Toe](https://github.com/BornaSepic/Tic-Tac-Toe)
repository. This project uses some of the DevOps practices we've leaned
to build a complete automated software delivery process with pipelines.

## Used Practices

- Phases of SDLC: they are integrated into the project, it includes
planning, design, development, testing, deployment, and maintenance
- Source control: the project is build within this git repository,
using branching, commits, workflows and others
- Branching strategies: they are used for organized development with
bug-free code
- Building Pipelines: the steps possible for automation are defined
in a pipeline, so that the build process is autometed to ensure
consistency
- Continuous Integration: CI is integrated into the pipeline
- Continuous Delivery: CD practices are implemented to manually deploy
the app to production using Kubernetes
- Security: security practices are embeded throughout the pipeline,
automated tests are run whenever code changes are pushed to the repository
- Docker: the application is containerized using Docker, Dockerfile is
used to define the application's dependencies and runtime environment,
the Docker image is built and published to DockerHub
- Kubernetes: the containerized application is lovally deployed to a
Kubernetes cluster

## Additional Information

- The pipeline starts with a git repository
- The solution is T-shaped: we have a working horizontal and one deep
dive vertical at Docker
- The solution, where possible, is as code
- The documentation of the project is described here
- Mandatory components - Continuous Integration, Deploy to Kubernetes,
are included
- The tools that are used are: Git, GitHub Actions, Docker, Kubernetes,
some Security Pactices and others

## Process

- Project Planning: understand the requirements and expectations, create
a project plan, choose which practices to include in the project

The practices that are included in the solution of the project are:
Phases of SDLC, Source control, Branching strategies, Building Pipelines,
Continuous Integration, Continuous Delivery, Security, Docker, Kubernetes.

SDLC phase: Planning phase

- Source control: set up a git repository for the project

This repository is set up by forking [Tic-Tac-Toe](https://github.com/BornaSepic/Tic-Tac-Toe)
repository with the Tic Tac Toe application source code.

SDLC phase: Planning phase

- Branching strategies: choose a branching strategy that fits the project

I chose to have one branch "develop" for creating the automated software
delivery process, and merge it to the main branch when needed. So in this
step I created the "develop" branch and started to work there.

SDLC phase: Planning phase

- Style Checks: execute checks that are intended to enforce a consistent
coding style across the project

The process of the style checks included adding licence. contributing and
.editorconfig, and then executing flake8, editorconfig-checker and
mardownlint-cli. After fixing the inconcictencies of the files, I started my
workflow pipeline with these three security checks.

SDLC phase: Implementation and Testing Phase

- Testing: execute unit tests to ensure that the application logic is correct

I executed a few unit tests to see if the functions in the source code are
working as intended. When the unit tests were done and successfully executed,
I added them as the next step in the pipeline that first waits the style
checks to be completed.

SDLC phase: Testing Phase

- Security: integrate static code analysis (SAST) tools into the Cl pipeline

This includes using SAST tools for static code analysis. I implemented in
the workflow the following security checks: gitleaks for hardcoded secrets,
SonarCloudScan and SnykScan. For SonarCloudScan and SnykScan I created tokens,
as variables to grant access. They are executed in parallel with the unit tests.

SDLC phase: Implementation and Testing Phase

- Docker: write a Dockerfile to containerize the application, build and test
the Docker image locally, and then itegrate it to the pipeline with build and
publish to DockerHub

Using Docker practices I created Dockerfile, which I tested locally. After I
successfully built Docker image with the Dockerfile, and successfully exposed
the application on localhost, I implemented the built in the pipeline. After the
testing and security steps are completed, TrivyScan is executed for the Docker image,
and only after the scan is successfull the Docker image is built, and then published
to my DockerHub account. Locally you can start the app with the following commands:
1. docker build -t modern-devops-practices-project . # you should be in the root
directory
2. docker run -p 8000:80 modern-devops-practices-project # this will port the app
to http://localhost:8000/

SDLC: Implementation and Testing Phase

- Kubernetes: set up a local Kubernetes cluster

First I wrote Kubernetes manifests (deployment.yaml and service.yaml, using
NodePort for the connection) to define the application deployment. Then, I started
my Docker and Minikube. With all this being set, I executed the following commands:
1. docker build -t tic-tac-toe:latest .
2. docker tag tic-tac-toe:latest tic-tac-toe:latest
3. docker images # to verify that my local image is listed
4. kubectl apply -f deployment.yaml
5. kubectl get pods # ensure that the pod transitions to the Running state
6. kubectl apply -f service.yaml
7. minikube service tic-tac-toe-service # the app should automatically be opened in
browser
Following this step, the app is successfully deployed to Kubernetes cluster.

SDLC phase: Implementation and Testing Phase

- Continuous Integration: GitHub Action CI tool is used to set up a basic
build pipeline

I built the pipeline in parallel with doing the rest of the task. Each step
that needed automation is implemented in the workflow. The CI part of the
pipeline includes: style checks, testing, security and docker.

SDLC phase: Implementation Phase

- Continuous Delivery: manually deploy the app to a Kubernetes cluster

I have a separate manual step for deploying to production after successful
testing in staging. The final deployment to production is initiated manually.
If the pipeline included fully automated deployment to production without manual
intervention, it would be referred to as Continuous Deployment.

SDLC phase: Implementation and Testing Phase

- Documentation: document each step of the solution

I wrote the documentation while I was doing the taks, so it would be consistent.
At the end I ensured that your documentation is complete and up-to-date.

SDLC phase: Documentation Phase
