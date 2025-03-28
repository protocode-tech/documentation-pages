---
title: 'Pausing not triggered'
---

While the project configuration is set to [automatically pause](/project-configuration/pausing#automatic-trigger) an environment after a certain period of inactivity, my environment remains continuously open.

As a reminder, an environment is considered inactive if there are no active SSH or HTTP connections. If an environment does not pause, it is typically because either an IDE is still connected, or someone is viewing a preview URL. So, check that no IDE is connected and that no one (or third-party service) is currently viewing the URLs exposed by the environment.

If the problem persists, don't forget that you can still manually trigger the pause, and [contact support](/resources-and-support/contact-support).
