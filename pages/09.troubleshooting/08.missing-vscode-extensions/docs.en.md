---
title: 'My VSCode extension are not installed'
---

When connecting to an environment, you cannot find your usual extensions.

This is actually completely normal. Your local IDE only serves as an interface with the environment, which has a "clean" instance of Visual Studio Code. No extensions are installed there. However, you can make the necessary extensions for the project be automatically installed. To do this, you need to add a call to `code --install-extension <extension_id>` in the lifecycle of the corresponding repository:

[prism classes="language-bash"]
# In the "Before container build" event
code --install-extension vue.volar
[/prism]
