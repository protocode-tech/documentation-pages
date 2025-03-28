---
title: 'Add a Git repository'
taxonomy:
    category:
        - docs
---

In Protocode, we distinguish between projects and GIT repositories, although these concepts often overlap. A project is a global concept that encompasses one or more sources, as well as tasks and team members.

When a project is created, the second step is to add the repositories. For monolithic projects, there will only be one. But in complex projects, there may be several. For example, one repository for an API, and another for a JavaScript site that consumes the API.

Adding a repository is done in 3 steps:

* **Identification**: fill in the URL of the repository. The URL can be from a repository hosted on GitHub, but also GitLab (public or private), or BitBucket.

* **Assigning read and write rights to Protocode**. Protocode will generate an SSH key that needs to be added as a deployment key **with write rights**.

* **Choosing the default branch**: the branch where the user will be placed when opening an environment.

Once these steps are completed, Protocode can retrieve and push changes to the source code, but it is not yet able to execute it. This will be handled in the next step: virtualization.
