---
title: 'Startup process stuck'
media_order: 'process_show_FR.png,process_create_server.png,process_error_FR.png,process_show_EN.png,process_error_EN.png'
---

After clicking the **"Start"** button for an environment, the process seems to freeze at a certain step and does not progress after several minutes.

### Check the process status

Start by displaying the logs to see **at which step** the process is stuck and what the **command outputs** are.

![process_show_EN](process_show_EN.png?style=max-width:25rem;)

### Blocking Commands

The most common case is a **blocking command** in the project lifecycle, such as the compilation of a **JavaScript** application.

- If a command **runs a continuous process**, the start will remain blocked.  
- **Solution:**  
  - Interrupt the startup.  
  - Remove the command from the executed script at launch.  
  - Move it into the **docker-compose** file as a [service command](https://docs.docker.com/reference/compose-file/services/#command):

[prism classes="language-yaml line-numbers" highlight="12"]
version: '3.8'
services:
  app:
    image: node:16
    volumes:
      - .:/app
    working_dir: /app
    ports:
      - '80'
    environment:
      VIRTUAL_HOST: "app-my-repository.${ENVIRONMENT_URL}"
    command: npm run dev # The command will no longer block the lifecycle
[/prism]

👉 **Alternative**: Run the command manually from your IDE's terminal once the environment is up.

### Server Provisioning

If a large number of users launch environments at the same time, **Protocode may need to provision a new server**.
This step usually takes about 90 seconds.

![process_create_server](process_create_server.png?style=max-width:35rem;)

If the server is still not ready after 5 minutes, [contact support](/resources-and-support/contact-support).

## Process Error

If after clicking **"Start"**, the process stops abruptly and a **red icon** appears, this means that **an error prevented the launch**.

![process_error_EN](process_error_EN.png?style=max-width:25rem;)

View the logs by clicking the red icon to identify the source of the problem.

### Error in a Lifecycle Command

The most frequent error is due to an incorrect command in the lifecycle steps.

Check the logs, identify the error, and correct the corresponding script.

### Issue with Docker Registry

If the **registry** (the service that stores the Docker images for the project) is temporarily inaccessible for **maintenance**, the start may fail.

* **Check its status** on the [service status page](https://status.protocode.tech/)
* If the service is **in red**, wait a few minutes and try again.

If the problem persists, [contact support](/resources-and-support/contact-support).
