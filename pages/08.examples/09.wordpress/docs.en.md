---
title: 'WordPress project'
taxonomy:
    category:
        - docs
---

Here is an example of a WordPress project configured with Protocode:

[https://github.com/protocode-tech/wordpress-template](https://github.com/protocode-tech/wordpress-template)

## Project Content

It contains a `.protocode` directory that holds all the configuration:

[prism classes="language-text" highlight="2,3,4,5,6,7"] 
└── wordpress-template/
   ├── .protocode/
   │  └── .env
   │  └── docker-compose.yml
   │  └── Dockerfile
   │  └── lifecycle/
   │    └── postUp.sh
   │ ... Rest of the files
[/prism]

* The **.env** file contains the environment variables used by docker-compose.
* The **docker-compose.yml** file contains the Docker Compose configuration. It creates an app container based on PHP 8.1, exposes it publicly, creates a container for the database, manages file synchronization between the container and the host machine, and adds the most relevant [Docker aliases](/project-configuration/docker-aliases).
* The **Dockerfile** describes the build steps for the app container, installing all dependencies (PHP, Apache, Composer, etc.).
* The **lifecycle** folder contains the project's initialization scripts. The `preUp.sh` file creates the necessary configuration files for WordPress and handles any permission issues.

## How to Use It

In a similar project, you can either:
- **Version the files in your repository and reference them in the repository configuration on Protocode**. Retrieve the content of this directory and version it within your project, then in the Protocode repository virtualization configuration, select "Use the docker-compose file within the repository", and specify the location `.protocode/docker-compose.yml`. Then, in the "Initialization" section, under "Before container build", place `.protocode/lifecycle/preUp.sh`.
- **Copy the content of the files into the repository configuration on Protocode without versioning them in the project**. In the Protocode repository virtualization configuration, select "Create a custom docker-compose file", paste the content of `.protocode/docker-compose.yml` into the form field. Then, in the "Initialization" section, under "Before container build", paste the content of `.protocode/lifecycle/preUp.sh`.
