---
title: 'Error 404 on preview URLs'
media_order: error_404.png
---

When you visit the preview URL of an environment, the server may return a 404 error like this:

![error_404](error_404.png?style=max-width:35rem;)

This means that the environment is responding, but no container is found for this URL.

## Checking the Container Status

The problem may be due to the container encountering an error during startup. You can check if it's running properly with the following command:

[prism classes="language-bash"]
docker-compose ps <service_name>
[/prism]

Example:
[prism classes="language-bash"]
$ docker-compose ps app
NAME     IMAGE     COMMAND                  SERVICE      CREATED        STATUS         PORTS
my_app   php-7.4   "/usr/local/bin/entr…"   app          5 mins ago     Up 5 mins      80/tcp
[/prism]

* **If the status is "Up"**, the container is working properly.
* **If the status is "Restarting"**: it's encountering an issue during startup.

## Viewing Container Logs

If your container is restarting in a loop, you can check its logs to identify the error:

[prism classes="language-bash"]
$ docker-compose logs <service_name> -f
[/prism]

The output logs will give you valuable insights into the root cause of the issue.

## Common Causes of the Issue

1. **Missing Dependencies**

Ensure that all dependencies are properly installed. For example:
[prism classes="language-bash"]
$ composer install # For PHP projects
$ npm install # For JavaScript projects
[/prism]

2. **Necessary Processes to Launch**

Some applications require compilation before they are functional. For example:
[prism classes="language-bash"]
$ npm start # For JavaScript applications
$ php artisan serve # For Laravel projects
[/prism]

3. **Routing Issue**

Make sure that routing to the container is correctly configured. Check the [routing rules](/project-configuration/containers-routing).

4. **Outdated Link**

It is possible that the environment has been paused, and the link you are accessing is outdated. Go back to the corresponding task and click on the preview link to get an updated one.

## Need Help?

If the issue persists, [contact support](/resources-and-support/contact-support).
