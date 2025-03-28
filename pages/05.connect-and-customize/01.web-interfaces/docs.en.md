---
title: 'Web Interfaces'
taxonomy:
    category:
        - docs
media_order: 'vscode_web.png,preview_FR.png,code_web_FR.png,code_web_EN.png,preview_EN.png'
---

Protocode offers flexible interfaces that allow you to connect your usual tools to the open environments, so you can continue working without changing your habits.

## **Web IDE**

This interface is fixed and always available. It is a portable version of Visual Studio Code. You can access it from the "Coder" context menu of a task by clicking on "Open Web IDE."

![code_web_EN](code_web_EN.png?style=max-width:25rem;)

This web implementation of Visual Studio Code offers the same possibilities as the software version. You can add the same extensions, open terminals, download files, and do everything you would normally do locally but through your browser.

![vscode_web](vscode_web.png "vscode_web")

It is very useful for quickly intervening in code reviews or for allowing other developers to come help you debug an issue (by providing them with the URL to the interface).

## **Preview URLs**

Depending on the settings entered in the [Virtualization](/project-configuration/containers-routing) section of each repository, certain containers are exposed. Protocode lists all these containers and their associated preview URLs. These can be found in the context menu of each assignment.

![preview_EN](preview_EN.png?style=max-width:25rem;)

!!! Even though these URLs are present in the menu, this does not necessarily mean that the associated application is running. For example, with JavaScript applications, you will first need to connect to the environment and run the compilation from the Node container.

These preview URLs allow both the developer and the task supervisor to test the execution of the produced code without needing to deploy it. This is also a very useful tool when developing an application that communicates bilaterally with third-party tools (such as online payment services), often via webhooks.

## **Persistent Preview Links**

To the right of each link, you will find a "Persistent Link" button that provides you with a public URL. This URL will automatically reopen the environment if it is closed or paused. You can share this link with a tester, allowing them to view the results at their convenience without any action required on your part and without needing to sign up.
