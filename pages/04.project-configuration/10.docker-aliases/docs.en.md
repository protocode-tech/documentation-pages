---
title: 'Docker aliases'
taxonomy:
    category:
        - docs
media_order: 'alias_up_FR.png,alias_portee_FR.png'
---

`FEATURE IN BETA`

The proposal is to abstract Docker in the terminal when you are at the root of a repository. To do this, Protocode offers to automatically create terminal aliases that allow you to call executables inside containers as if they were on the host machine.

Let’s take an example. Imagine a repository uses an image with NodeJS. To call it, you would normally run a command like this:

[prism classes="language-bash"]
$ docker-compose run --rm app node --version
v16.0.0
[/prism]

With aliases, you can simply type:

[prism classes="language-bash"]
$ node --version
v16.0.0
[/prism]

## Declaring Aliases

Aliases are declared directly in the docker-compose file, within a container, under the "labels" key. 
`protocode.alias.{{ executable_name }}`: `equivalent docker-compose command`.

[prism classes="language-yaml line-numbers" highlight="8,9"]
# docker-compose.yml file for the repository
version: '3.8'
services:
  app:
    image: "node:16"
    ...
    labels:
      protocode.alias.node: docker-compose run --rm app node
      protocode.alias.npm: docker-compose run --rm app npm
[/prism]

This will result in the aliases being installed when the containers start:

![alias_up_FR](alias_up_FR.png?style=max-width:35rem;)

## Scope of Aliases

The aliases created in this way only take effect at the root of the repository where the docker-compose file that created them is located.

Here’s what happens if you navigate to the parent directory:

![alias_portee_FR](alias_portee_FR.png?style=max-width:25rem;)

## Automatic Generation

In projects automatically configured by AI, as well as projects using Protocode’s pre-configured images, the relevant aliases are automatically added. For Laravel or Symfony projects, beyond php, it is even possible to directly call artisan or bin/console.
