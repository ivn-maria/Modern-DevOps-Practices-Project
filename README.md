# Final Project

The application I am working with is a simple Tic Tac Toe Game web-based
application that i got from [Tic-Tac-Toe](https://github.com/BornaSepic/Tic-Tac-Toe)
repository. This project uses some of the DevOps practices we've leaned
to build a complete automated software delivery process with pipelines.

## Used Practices

1. Phases of SDLC
Software development lifestyle phases are integrated into the project and
include: plan, code, build, test, release, deploy, operate, monitor.
2. Source control
The project is built within this git repository, using branching, commits,
workflows and others.
3. Branching strategies
They are used for organized development with bug-free code.
4. Building Pipelines
The steps possible for automation are defined in a pipeline, so that the
build process is autometed to ensure consistency.
5. Continuous Integration
CI is integrated into the pipeline.
6. Continuous Delivery
CD practices are implemented to manually deploy the application to
production using Kubernetes.
7. Security
Security practices are embeded throughout the pipeline, automated tests are
run whenever code changes are pushed to the repository.
8. Docker
The application is containerized using Docker, Dockerfile is used to define
the application's dependencies and runtime environment, the Docker image is
built and published to DockerHub.
9. Kubernetes
The containerized application is locally deployed to a Kubernetes cluster.

## Additional Information

- The pipeline starts with a git repository
- The solution is T-shaped: we have a working horizontal and one deep
dive vertical at CI
- The solution, where possible, is as code
- The documentation of the project is described here
- Mandatory components - Continuous Integration, Deploy to Kubernetes,
are included
- The tools that are used are: Git, GitHub Actions, Docker, Kubernetes,
some Security Pactices and others

## Steps of Building the Solution

### Project Planning

Task: understand the requirements and expectations, create
a project plan, choose which practices to include in the project

Process: The practices that are included in the solution of the project are:
Phases of SDLC, Source control, Branching strategies, Building Pipelines,
uous Integration, Continuous Delivery, Security, Docker, Kubernetes.

SDLC phase: Plan

### Source control

Task: set up a git repository for the project

Process: This repository is set up by forking [Tic-Tac-Toe](https://github.com/BornaSepic/Tic-Tac-Toe)
repository with the Tic Tac Toe application source code.

SDLC phase: Code (it involves managing and tracking changes to the codebase)

### Branching strategies

Task: choose a branching strategy that fits the project

Process: I chose to have one branch "develop" for creating the automated software
delivery process, and merge it to the main branch when needed. So in this
step I created the "develop" branch and started to work there.

SDLC phase: Code (they belong to organizing and managing code branches)

### Style Checks

Task: execute checks that are intended to enforce a consistent coding style across
the project

Process: The process of the style checks included adding licence. contributing and
.editorconfig, and then executing flake8, editorconfig-checker and
mardownlint-cli. After fixing the inconsistencies of the files, I started my
workflow pipeline with these three security checks.

SDLC phase: Code (they ensure code consistency and adherence to coding
standards during the coding phase)

### Testing

Task: execute unit tests to ensure that the application logic is correct

Process: I executed a few unit tests to see if the functions in the source code are
working as intended. When the unit tests were done and successfully executed,
I added them as the next step in the pipeline that first waits the style
checks to be completed.

SDLC phase: Test

### Security

Task: integrate static code analysis tools into the Cl pipeline

Process: This includes using SAST tools for static code analysis. I implemented in
the workflow the following security checks: gitleaks for hardcoded secrets,
SonarCloudScan and SnykScan. For SonarCloudScan and SnykScan I created tokens,
as variables to grant access to the security tools. They are executed in parallel
with the unit tests in the pipeline.

SDLC phase: Operate (it is an ongoing consideration throughout the SDLC but
becomes critical during the operational phase)

### Docker

Task: write a Dockerfile to containerize the application, build and test
the Docker image locally, and then itegrate it to the pipeline with build and
publish to DockerHub

Process: Using Docker practices I created Dockerfile, which I tested locally. After
I successfully built Docker image with the Dockerfile, and successfully exposed
the application on localhost, I implemented the built in the pipeline. After the
testing and security steps are completed, TrivyScan is executed for the Docker image,
and only after the scan is successfull the Docker image is built, and then published
to my DockerHub account. Locally you can start the app with the following commands:

1. docker build -t modern-devops-practices-project . # should be executed in the
root directory
2. docker run -p 8000:80 modern-devops-practices-project # this will port the app
to [localhost:8000](http://localhost:8000/)

SDLC: Build, Deploy (it is involved in building containerized applications and
deploying them in consistent environments)

### Kubernetes

Task: set up a local Kubernetes cluster

Process: First I wrote Kubernetes manifests (deployment.yaml and service.yaml, using
NodePort) to define the application deployment. Then, I started my Docker and
Minikube. With all this being set, I executed the following commands:

1. docker build -t tic-tac-toe:latest .
2. docker tag tic-tac-toe:latest tic-tac-toe:latest
3. docker images # to verify that my local image is listed
4. kubectl apply -f deployment.yaml
5. kubectl get pods # ensure that the pod transitions to the Running state
6. kubectl apply -f service.yaml
7. minikube service tic-tac-toe-service # the app should automatically be opened
in browser
Following these steps, the app is successfully deployed to a Kubernetes cluster.

SDLC phase: Release, Deploy, Operate (it defines how your application should be
represented and configured for deploymenit, it is also primarily associated with
deploying and operating containerized applications in a production environment)

### Continuous Integration

Task: use GitHub Action CI tool to set up a basic build pipeline

Pocess: I built the pipeline in parallel with doing the rest of the task. Each step
that needed automation is implemented in the workflow. The CI part of the
pipeline includes: style checks, testing, security and docker.

SDLC phase: Build, Test (it involves automatically integrating code changes and
running tests to ensure code quality)

### Continuous Delivery

Task: manually deploy the app to a Kubernetes cluster

Process: I have a separate manual step for deploying to production after successful
testing in staging. The final deployment to production is initiated manually.
If the pipeline included fully automated deployment to production without manual
intervention, it would be referred to as Continuous Deployment.

SDLC phase: Release, Deploy (it releases and deploy of applications to different
environments)

### Documentation

Task: document each step of the solution

Process: I wrote the documentation while I was doing the taks, so it would be consistent.
At the end I ensured that your documentation is complete and up-to-date.

SDLC phase: Operate (it is ongoing but becomes particularly important during the
operational phase to guide and support ongoing operations)

## Continuous Integration Vertical Deep Dive

### Definition

Continuous integration is a DevOps software development practice where
developers regularly merge their code changes into a central repository,
after which automated builds and tests are run. Continuous integration most
often refers to the build or test stage of the software development lifecycle.
The key goals of continuous integration are to find and address bugs quicker,
improve software quality, and reduce the time it takes to validate and release
new software updates.

### Benefits

In the past, developers on a team might work in isolation for an extended
period of time and only merge their changes to the master branch once their
work was completed. This made merging code changes difficult and time-consuming,
and also resulted in bugs accumulating for a long time without correction.
These factors made it harder to deliver updates to customers quickly.
Continuous integration helps your team be more productive by freeing developers from
manual tasks and encouraging behaviors that help reduce the number of errors and
bugs released to customers.
With more frequent testing, your team can discover and address bugs earlier before
they grow into larger problems later.
Continuous integration helps your team deliver updates to their customers faster
and more frequently.

### Continuos Delivery

With continuous integration, developers frequently commit to a shared repository
using a version control system such as Git. Prior to each commit, developers may
choose to run local unit tests on their code as an extra verification layer before
integrating. A continuous integration service automatically builds and runs unit
tests on the new code changes to immediately surface any errors.
Continuous integration refers to the build and unit testing stages of the software
release process. Every revision that is committed triggers an automated build and
test. With continuous delivery, code changes are automatically built, tested, and
prepared for a release to production. Continuous delivery expands upon continuous
integration by deploying all code changes to a testing environment and/or a
production environment after the build stage.
