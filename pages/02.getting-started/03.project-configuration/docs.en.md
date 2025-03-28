---
title: 'Setup a project'
taxonomy:
    category:
        - docs
---

In the "Projects" section, click the "Create" button at the top right and fill in the requested information. You will then be redirected to the project administration page, in the "Configuration" section.

## Adding a Source

In the "Git Repositories of the Project" block, click the "Add" button, then enter the repository address. Copy the generated SSH key and add it as a deployment key with write access to your repository. Click "Continue", select the default branch, and then click "Continue" again.

## Virtualization

You will be redirected to the _Virtualization_ section. Click "Launch AI" and wait until the Docker configuration is generated (maximum 2 minutes). You will then be prompted to build the project's Docker images. The process will start automatically, and you should wait until the process finishes (maximum 5 minutes).

## Initialization

Once the pre-build process is complete, you will be redirected to the _Initialization_ section to initiate caching. The process will start automatically, and you should wait until the process finishes (maximum 2 minutes). Your project is now fully configured, and you can click "Close" at the bottom right.  
