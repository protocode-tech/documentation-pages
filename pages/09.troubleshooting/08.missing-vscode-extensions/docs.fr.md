---
title: 'Mes extensions VSCode ne sont pas installées'
---

En vous connectant à un environnement, vous ne trouvez pas vos extensions habituelles.

C'est en réalité tout à fait normal. Votre IDE local ne sert que d'interface avec l'environnement, qui lui a une instance de Visual Studio Code "vierge". Aucune extension n'y est installée. Néanmoins, vous pouvez faire que les extensions nécessaires au projet soient automatiquement installées. Pour cela il vous faut ajouter dans le cycle de vie du dépôt correspondant un appel à `code --install-extension <id_extension>`:

[prism classes="language-bash"]
# Dans l'évènement "Avant la construction des conteneurs"
code --install-extension vue.volar
[/prism]