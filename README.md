# npm-version-github-action
Test de l'utilisation de npm version avec les github action pour faire des releases

Le workflow suivant https://github.com/kerphi/npm-version-github-action/blob/main/.github/workflows/create-release.yml utilise workflow_dispatch pour demander le n° de release a l'utilisateur par formulaire et ensuite va faire un "sed" la ou il faut dans le code, il le commit, puis crée un tag git et git push le tout. Ce workflow est pas mal car on contrôle très bien ce qu'on fait quand on génère une version et on peut embarquer des commandes shell dans le workflow qui sont très lisibles.

Le workflow suivant https://github.com/kerphi/npm-version-github-action/blob/main/.github/workflows/bump.yml utilise le module 'phips28/gh-action-bump-version@master' qui d'automatiquement "bumper" le n° de version quand on fait un push en parsant les commentaires pour savoir si c'est un patch, minor ou major. Ce workflow est intimement lié à "npm version" et donc aux projets avec nodejs. C'est pas terrible car il n'est pas générique par rapport à une appli java (pom.xml) et ca peut être perturbant de générer automatiquement des numéro de version à chaque push (même si ce dernier point est probablement paramétrable) !

A noter qu'on peut chaîner les workflow pour par exemple enchainer avec un build-test-push une fois qu'une nouvelle release a été créée. cf https://github.com/kerphi/npm-version-github-action/blob/main/.github/workflows/ci.yml#L3-L11 Ceci peut être cumulé avec un evenement de type push classique sans release ce qui permet de builder une version sans numéro de version et au moment ou on génère une version de builder également.

---

Test pour patch du README avec la version de l'appli: 1.3.0



.
.
