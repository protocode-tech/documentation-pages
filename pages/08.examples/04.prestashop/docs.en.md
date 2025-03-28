---
title: 'Prestashop project'
taxonomy:
    category:
        - docs
---

Here is an example of a Prestashop project configured with Protocode:

[https://github.com/protocode-tech/prestashop-template](https://github.com/protocode-tech/prestashop-template)

## Project Content

It contains a `.protocode` directory that holds all the configuration:

[prism classes="language-text" highlight="2,3,4,5,6,7"] 
└── prestashop-template/
   ├── .protocode/
   │  └── .env
   │  └── docker-compose.yml
   │  └── Dockerfile
   │  └── lifecycle/
   │    └── postUp.sh
   │ ... Rest of the files
[/prism]

* The **.env** file contains the variables used by docker-compose.
* The **docker-compose.yml** file contains the Docker Compose configuration. It creates an app container based on PHP 8.1, exposes it publicly, a container for the database, manages file synchronization between the container and host machine, and adds the most relevant [Docker aliases](/project-configuration/docker-aliases).
* The **Dockerfile** file describes the steps for building the app container and installs all the dependencies (PHP, Apache, Composer, etc.).
* The **lifecycle** folder contains the project's initialization scripts. The `preUp.sh` file creates the configuration files and folders expected by Prestashop and resolves any permission issues.

## How to Use It

In a similar project, you can copy the contents of the `.protocode` folder into your project, version it, and reference it in the repository configuration on Protocode. Retrieve the content of this directory and version it within your project, then in the Protocode repository virtualization configuration, select "Use the docker-compose file within the repository", and specify the location `.protocode/docker-compose.yml`. Then, in the "Initialization" section, under "Before container build", place `.protocode/lifecycle/preUp.sh`.