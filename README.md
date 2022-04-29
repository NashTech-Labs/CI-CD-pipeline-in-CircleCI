# CI-CD-pipeline-in-CircleCI

**What is a CI/CD pipeline?**

A CI/CD pipeline automates your software delivery process. The pipeline builds code, runs tests (CI), and safely deploys a new version of the application (CD).
Automated pipelines remove manual errors, provide standardized feedback loops to developers, and enable fast product iterations.

CI, short for Continuous Integration, is a software development practice in which all developers merge code changes in a central repository multiple times a day. CD stands for Continuous Delivery, which on top of Continuous Integration adds the practice of automating the entire software release process.

With CI, each change in code triggers an automated build-and-test sequence for the given project, providing feedback to the developer(s) who made the change. The entire CI feedback loop should run in less than 10 minutes.

Continuous Delivery includes infrastructure provisioning and deployment, which may be manual and consist of multiple stages. What’s important is that all these processes are fully automated, with each run fully logged and visible to the entire team.

**CircleCI**
CircleCI is the continuous integration & delivery platform that helps development teams to release code rapidly and automate the build, test, and deploy process using Docker container. CircleCI is a reliable platform that works well with languages like Ruby, Python, NodeJS, Java and Clojure.

CircleCI believes in configuration as code. Your entire CI/CD process is orchestrated through a single file called config.yml. The config.yml file is located in a folder called .circleci at the root of your project. CircleCI uses the YAML syntax for config. See the Writing YAML document for a basic introduction.

Your CircleCI configuration can be adapted to fit many different needs of your project. The following terms, sorted in order of granularity and dependence, describe the components of most common CircleCI projects:

Pipeline: Represents the entirety of your configuration. (not available for server v2.x)
Workflows: Responsible for orchestrating multiple jobs.
Jobs: Responsible for running a series of steps that perform commands.
Steps: Run commands (such as installing dependencies or running tests) and shell scripts to do the work required for your project.

**Components on CircleCI**

1. ORBS: Orbs are reusable snippets of code that help automate repeated processes, accelerate project setup, and make it easy to integrate with third-party tools
2. Executors: CircleCI offers several execution environments. We call these executors. An executor defines the underlying technology or environment in which to run a job. Set up your jobs to run in the docker, machine, macos or windows executor and specify an image with the tools and packages you need.

**Steps to Signup with CircleCI**

1. Signing up with CircleCI using GitHub or Bitbucket is free.
2. Now time to authorize CircleCI to access your code base using repositories by clicking the “ADD PROJECTS” on CircleCI console.
3. After this add the repositories you want to build from your GitHub.
4. Configure CircleCI automatically analyzes your code settings and works fine most of the time. But if it doesn’t work then you need to configure the circle.yml file. This file helps and informs CircleCI about the exact action a user intends to perform on his build. This is a simple YAML file where you need to put the build steps as per CircleCI file structure and content. The other additional steps like initializing circle.yml is done by placing the YAML file in the repo’s root directory and then CircleCI reads the file each time it runs a build using the YAML file. Also, circle.yml file is completely optional. You will override this file by using the additional GUI option. But if by mistake you define “Test Commands” in GUI and also inherit circle.yml in your code then CircleCI will infer variables, environment etc from your circle.yml
5.Now clone this repo and make changes in CircleCI template as per your pipeline requirement specially in AWS in this template we have four stages:
  a. Build: Build part build docker file and push AWS ECR
  b. Deploy: Deploy part deploy micro service as deployment in AWS EKS.
  c. Restart: Restart part restart the pods to get changes.
  d. Health: Health part check healthyness of deployment after deploying service.
6. Now add ENV in project in CircleCI GUI.

