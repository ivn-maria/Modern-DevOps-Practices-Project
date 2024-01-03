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
- Continuous Delivery: CD practices are implemented to automatically
deploy code changes to staging or production environments after
successful CI
- Security: security practices are embeded throughout the pipeline,
automated tests are run whenever code changes are pushed to the repository
- Docker: the application is containerized using Docker, Dockerfile is
used to define the application's dependencies and runtime environment,
the Docker image is built and published to DockerHub
- Kubernetes: the containerized application is deployed to a Kubernetes
cluster

## Additional Information

- The pipeline starts with a git repository
- The solution is T-shaped: we have a working horizontal and one deep
dive vertical at Docker
- The solution of most steps is as code
- The documentation of the project is described here
- Mandatory components - Continuous Integration, Deploy to Kubernetes,
are included
- The tools that are used are: Git, GitHub Actions, Docker, Kubernetes,
as well as some Security Pactices

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

- Security: integrate static code analysis (SAST) tools into the CI pipeline

This includes using SAST tools for static code analysis. I implemented in
the workflow the following security checks: gitleaks for hardcoded secrets,
SonarCloudScan and SnykScan. For SonarCloudScan and SnykScan I created tokens,
as variables to grant access. They are executed in parallel with the unit tests.

SDLC phase: Implementation and Testing Phase

- Docker: write a Dockerfile to containerize your application, build and test
the Docker image locally, and then itegrate it to the pipeline with build and
publish to DockerHub

Using Docker practices I created Dockerfile, which I tested locally. After I
successfully built Docker image with the Dockerfile, and successfully exposed the
application on localhost, I implemented these steps in the pipeline. After the
testing and security steps are completed, TrivyScan is executed for the Docker image,
and only after the scan is successfull the Docker image is built and then published
to my DockerHub account.

SDLC: Implementation and Testing Phase

- TO DO Kubernetes: set up a Kubernetes cluster (local or on a cloud provider).

Write Kubernetes manifests (YAML files) to define your application deployment.
Define Kubernetes manifests (YAML files) to specify how your application should
run, scale, and connect to other services. Use Kubernetes for orchestration and
management of containerized applications.

SDLC phase: Implementation and Testing Phase

- Continuous Integration: GitHub Action CI tool is used to set up a basic build
pipeline

I built the pipeline in parallel with doing the rest of the task. Each step that
could be automated is implemented in the CI workflow.

SDLC phase: Implementatioon Phase

- TO DO Continuous Delivery: expand the Cl pipeline to include deployment steps
to staging environments and implement automated deployment scripts or tools

SDLC phase: Implementation and Testing Phase

- Documentation: document each step of the solution

I wrote the documentation while I was doing the taks, so it would be consistent.
At the end I ensured that your documentation is complete and up-to-date.

SDLC phase: Documentation Phase
