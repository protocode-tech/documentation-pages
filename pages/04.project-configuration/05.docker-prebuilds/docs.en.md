---
title: 'Docker Prebuilds'
taxonomy:
    category:
        - docs
media_order: 'docker_prebuild_FR.png,docker_prebuild_ok_FR.png,docker_prebuild_ok_EN.png,docker_prebuild_EN.png'
---

When the configuration involves custom Docker images, Protocode requires that the images be pre-built and stored in our registry to ensure that environments start as quickly as possible.

## Preconstruction Launch

If preconstruction is required, Protocode will display the following prompt:

![docker_prebuild_EN](docker_prebuild_EN.png?style=max-width:35rem;)

Simply click on the **"New build"** button to start the process. The output logs will then be displayed so you can monitor the progress and any errors that may occur.

If the preconstruction is successful, a message will appear, and the process will be marked as **"Succeeded"**.

![docker_prebuild_ok_EN](docker_prebuild_ok_EN.png?style=max-width:35rem;)

## Configuration Modification and Rebuild

If you modify the files involved in the Docker configuration for the project, you will need to restart the process to rebuild the images with the updated configuration. There is no automation for this. The update will affect all newly opened or restarted environments, but not those already open (if necessary, pause them and restart).
