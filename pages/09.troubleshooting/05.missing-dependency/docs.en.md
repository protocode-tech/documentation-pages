---
title: 'Missing dependency in the environment'
---

When starting an environment, an error of the type `<binary> not found` is returned. This means that you are trying to execute a binary that is not installed in the environment.

## Calling an Uninstalled Binary

As a reminder, the environment on Protocode is a Debian 11 machine that only includes a certain number of [tools necessary for its operation](/connect-and-customize/environment-anatomy#preinstalled-tools). You can certainly add more, particularly by calling `apt` or `apt-get`, and this can be done automatically during the [lifecycle of an environment](/project-configuration/setup-scripts#lifecycle-events) to ensure it happens when the environment starts.

## Positioning Issue

It can also happen that we forget that from a terminal, we are in the environment (host machine) and not in the application container, and vice versa.

Let’s take the example of a JavaScript project. Calling `npm install` from a new terminal should result in an "_npm not found_" error. To run npm, you would need to execute a `docker-compose` command like `docker-compose run --rm app npm install`, since npm runs inside the container, not in the environment.

Conversely, if I position myself inside a container with a command like `docker-compose exec app bash`, then call `git`, it is likely that a "git not found" error will be returned, because git is not installed in my container, but in the environment. The solution is either to run an `exit` command to return to the environment's terminal or to open a new terminal window.
