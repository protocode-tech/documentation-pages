---
title: 'Angular project'
taxonomy:
    category:
        - docs
---

Here is an example of an Angular project configured with Protocode:

[https://github.com/protocode-tech/angular-template](https://github.com/protocode-tech/angular-template)

## Project Content

It contains a `.protocode` directory that holds all the configuration:

[prism classes="language-text" highlight="2,3,4,5,6"] 
└── angular-template/
   ├── .protocode/
   │  └── docker-compose.yml
   │  └── lifecycle/
   │    └── preUp.sh
   │    └── postUp.sh
   │ ... Rest of the files
[/prism]

* The **docker-compose.yml** file contains the Docker Compose configuration. It creates an app container based on Node 16, exposes it publicly, manages file synchronization between the container and host machine, and adds the most relevant [Docker aliases](/project-configuration/docker-aliases).
* The **lifecycle** folder contains the project's initialization scripts. The `preUp.sh` file installs the dependencies in the `node_modules` folder, and the `postUp.sh` file installs the official Angular extension for VSCode.

## How to Use It

In a similar project, you can either:
- **Version the files in your repository and reference them in the repository configuration on Protocode**. Retrieve the contents of this directory and version it within your project, then in the Protocode repository virtualization configuration, select "Use the docker-compose file within the repository", and specify the location `.protocode/docker-compose.yml`. Then, in the "Initialization" section, under "Before container build", place `.protocode/lifecycle/preUp.sh`, and under "After container build", place `.protocode/lifecycle/postUp.sh`.
- **Copy the file contents into the repository configuration on Protocode without versioning them in the project**. In the Protocode repository virtualization configuration, select "Create a custom docker-compose file", and paste the contents of `.protocode/docker-compose.yml` in the form field. Then, in the "Initialization" section, under "Before container build", paste the contents of `.protocode/lifecycle/preUp.sh`, and under "After container build", paste the contents of `.protocode/lifecycle/postUp.sh`.
