---
title: Projects
visible: true
taxonomy:
    category:
        - docs
---

The project is the broadest object. It encompasses Git repositories, team members, tasks, and their assignments.  
Without discussing the addition of repositories (which is described in the [Configuration]( /project-configuration/add-git-repository) section), we will here describe how to manage a project in Protocode from an organizational perspective.

## Managing Team Members

Any person added as a member of the workspace can be added as a member of a project. To do so, simply go to the project page, click on the "Team" tab, and then click the "Create" button. When you click the button, a modal will open, inviting you to select a workspace member, a date range during which they will be involved (optional), and a profile. The profile system within a project is very similar to the one for [workspace members](/workspace-administration/members).

| Profile | Description |  
| ------- | ----------- |  
| **Manager** | This profile grants the most rights on the project. The user can administer and view all members, repositories, tasks, and their assignments. |  
| **Developer** | This is an intermediate profile that gives the user the right to view all members, repositories, tasks, and their assignments, but with no administration rights. This is sufficient if the user's role is limited to starting an environment, coding, and updating the status of a task. |  
| **Guest** | This is the lowest profile, which only allows the user to view the tasks assigned to them. This is the best profile for involving an external party in the project. |  

!!! Similar to workspace members, it is possible to manually modify the rights granted by checking/unchecking the rights displayed in the modal. For example, you could allow a developer to modify repositories to restart a preconstruction or create tasks for others.

## Managing Tasks

Within a project, you can create as many tasks as necessary. These will appear on the project's page in the "Tasks" tab.

Each task created has several pieces of information that can be grouped into two categories:  
* **Task identification information**: This includes the name, description, and flag (feature/bug) of the task.  
* **Project management information**: This includes the status (open/closed), priority (from low to urgent), planned start and end dates, the estimated time to complete the work, and the person responsible for supervising the task (the "Supervisor").

By default, a task created will be identified as "Unassigned," meaning it has not yet been assigned to any team member. To assign the task, go to the task page (by clicking its name from the task list), then click the "Assign" button. A modal will open, allowing you to select a team member. Once the assignment is made, the task will have a status of "Pending." At the same time, the assigned person will receive an email notification to inform them. When they log into Protocode, the task will appear in "My Tasks," and they can start an environment specific to that task.

## Task Lifecycle

Once a person starts an environment, the status of the corresponding task is automatically updated to "In Progress." The work progress is also automatically updated to 10%.

When the work is complete, you can change the task status to "To Test," and the progress will automatically update to 80%. The supervisor (if assigned) will receive an email notification, and the task will disappear from the developer's list of tasks. It will appear in "My Supervisions" for the supervisor.

The supervisor can then change the status to "In Validation" to acknowledge receipt. After testing, they can mark the task as "Completed" or "Rejected."

If the task is completed, the progress is automatically set to 100%, and the environment can be closed. If changes have not been validated or pushed, the system will prompt the supervisor to do so.

If the task is rejected, the developer will receive a notification and the task will reappear in "My Tasks." The developer will then modify the task to set it back to "In Progress" and later to "To Test" after addressing the feedback.

## Task Scope

You are free to define the scope of the tasks you create. You can define them in a precise and targeted way, which will result in separate environments for each. Alternatively, you can broaden the scope and define tasks that correspond to a complete sprint or even the entire life of a project (effectively using a task as a permanent workstation).
