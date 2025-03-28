---
title: 'Releases notes'
---

## 03/21/2025: Environment Updates
* Updated Docker, Docker Compose, DinD, PHP, vendors, Git, Visual Studio Code, Codeserver.
* Added Docker Compose plugin, now allowing the use of `docker compose <command>`.

## 03/19/2025: Improvements and Fixes
* `VIRTUAL_HOST` is no longer required to expose a container; port allocation via "XXXX:XXXX" now also works.
* Improved restart process: allocated resources and sleep delays are now updated.
* Fixed an issue preventing an environment from restarting when the agent's user account had been deleted.

## 03/15/2025: Feature - Devcontainer
* Added the ability to configure a repository using an existing `devcontainer.json` file.

## 03/11/2025: Improvement - Automatic Process Execution
* Automatic execution of mandatory Docker prebuild and caching processes.

## 02/02/2025: Fix
* Fixed a permissions issue affecting the preconfigured Prestashop image.

## 01/15/2025: Feature - User Preference Synchronization
* Created a VSCode plugin that syncs themes, shortcuts, and preferences between the local instance and Protocode. It also syncs terminal aliases (bash, zsh) for Mac and Unix users.

## 12/06/2024: Feature & Fix - AI-Based Auto-Configuration
* Integrated a new module that automatically configures repositories using AI.
* Fixed a `docker-compose` error when launching an environment while the Docker network was not yet started.

## 12/13/2024: Improvement - New Preconfigured Image
* Added PHP 5.6 to the preconfigured images to support legacy projects.

## 07/05/2024: UI Redesign
* Completely revamped interface for smoother navigation between Workspaces and tasks, and simplified repository configuration screens.

## 12/06/2024: Improvement - New Preconfigured Images
* Added MongoDB, PostgreSQL, Mongo Express, Python, Go, and Java to the preconfigured repository setup options.

## 10/31/2024: Improvement - New Stacks in Demo Module
* Added Angular, Symfony, Laravel, and Drupal stacks to the demo module.

## 10/30/2024: Improvement - "Page Not Found" on Environments
* A new "Page Not Found" screen has been created for environments, helping users identify errors and common solutions more easily.

## 10/17/2023: Feature - Magic Links
* Introduced a new feature allowing users to access a paused environment via a dedicated URL.

## 09/13/2023: Feature - Demo Module
* Added a demo module enabling users to test the platform in real-world conditions from the homepage.

## 08/22/2023: Fix
* Fixed an issue with the calculation of open environments in a workspace when an error occurred while opening an environment.

## 06/30/2023: Improvement - Internationalization
* Redesigned homepage.
* Fully translated application, now available in English and French.

## 06/13/2023: Improvement - Environment Restart
* Errors occurring during the restart of paused environments are no longer blocking.

## 06/08/2023: Fixes
* Fixed an issue affecting VSCode web interface users, where environments were being paused unexpectedly.
* Fixed an issue causing environments to pause after adding a new repository to the project configuration.

## 06/05/2023: Improvement - Pause/Resume Process
* Changed the architecture used for pausing, reducing pause time by a factor of 5 and resume time by a factor of 4.

## 05/22/2023: Improvements - Preconfigured Image Volumes
* The virtualization configuration interface now allows users to modify/add/remove volumes in "Use Protocode Preconfigured Images" mode.

## 05/05/2023: Improvements - Rootless User & Preconfigured Images
* The rootless user `protocode` now has ID 1000 to simplify permission management with many Docker images using the same ID.
* All preconfigured images now use ID 1000 for their main process user (`www-data` for PHP, for example).
* The Prestashop and WordPress images have been enhanced for seamless integration with the Protocode ecosystem ("plug-n-play" versions).
* Added Node 20, PHP 8.2, Adminer, and MailDev to the preconfigured images.
* Fixed a bug preventing image prebuilding in repositories using `docker-compose` V1.

## 04/21/2023: Fix - Preview Links on Paused Environments
* Fixed an issue related to the dissociation of environments from repository configurations, which caused preview links to no longer appear in the web interface when resuming an environment.

## 04/20/2023: Improvement - Environment Restart
* Environment restarts are now independent of repository configurations, preventing configuration changes from blocking the restart of paused environments.

## 04/04/2023: Fix
* Fixed an issue related to the introduction of rootless environments where VSCode extensions were not installed via `code --install-extension`.

## 04/01/2023: Pricing Plan Changes
* Removed the Pay As You Go Individuals, Pay As You Go Enterprise, and Developer plans.
* Changed the Starter plan to a free plan, offering 50 monthly credits with no overage.
* Introduced the Pro plan at €9/month, providing 100 monthly credits, with overages billed at €0.18/credit.

## 03/23/2023: Feature - New Lifecycle Hook
* Added a new hook allowing custom processing before an environment goes to sleep.

## 02/16/2023: Fixes & Improvements
* Fixed the "Git Unsafe Repository" error.
* Improved the build process: precisely identifies which images need to be built and only builds those, without pulling other images from the `docker-compose` file. Prebuilding is no longer mandatory if all images are already built.

## 02/10/2023: Fixes & Minor Changes
* Fixed an error occurring when pausing environments with large modified files being compressed.
* Default `docker-compose` version changed from v1 to v2.
* Added links to the changelog and service status.
