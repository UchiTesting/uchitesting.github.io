Configuration SSH simplifié pour GitHub
=======================================

> Les instructions concernent Windows.

## Création d'un clé SSH

- Ouvrir GIT GUI

- Aller dans le menu *Help* > *Show SSH Key*.
Si il n'y a pas de clé disponible le bouton *Generate SSH Key* est disponible.
Il suffit de cliquer dessus. On se verra demander 2 fois une passphrase.
Saisir ce que l'on veut pour passphrase.

> La passphrase peut-être laissée vide. Dans ce cas l'utilisation est simplifiée mais moins sécurisée.  
> N'importe qui peut avoir accès aux dépôts GIT du compte lié sans problème.  
> Il est donc recommandé d'en saisir une.


- La clé s'affiche dans la zone de texte en dessous.
Un bouton *Copy To Clipboard* permet de la copier simplement.

## Ajout de la clé publique sur GitHub

> Les termes possiblement non exactes car je me base sur le site en anglais.

- Aller sur son profile GitHub puis dans les Paramètres

- Sur le menu de gauche aller dans le menu *Clés SSH et GPG* 

- Cliquer sur *Ajouter une clé SSH*.

- Donner un nom significatif au choix à la clé.
Elle sera facilement identifiable et supprimable par la suite.

- Coller la clé publique SSH dans la zone de texte et valider.

## Utilisation de la clé

La méthode décrite ci-dessus permet au moins de faire en sorte que GIT Bash trouve la clé
sans avoir à explicitement démarrer `ssh-agent`.

> Pour ne plus devoir saisir la passphrase à chaque fois, des étapes supplémentaires non couvertes ici sont nécessaires. 
> Il faudra entre autre ajouter la clé à l'aide de la commande `ssh-add` et configurer GIT Bash pour démarrer `ssh-agent` automatiquement.

La configuration est équilibrée entre simplicité et sécurité. Il faudra saisir la passphrase pour chaque action avec le remote.

On pourra au moins pull le travail une fois en fin de journée par exemple.

### Démarrer ssh-agent sur la session GIT Bash

Si on préfère, on peu au moins faire en sorte que la passphrase soit retenue dans la session courante.
Cela est pratique si on a quand même besoin d'utiliser GIT plus fréquemment.
Tant que la fenêtre de GIT Bash reste ouverte, la clé sera retenue.

Pour cela, il faut démarrer `ssh-agent`.

`eval $(ssh-agent -s)`

> Pro Tip: On pourrait aussi créer un alias. Pour Windows consulter la configuation de GIT à cette fin.

Ensuite on peu ajouter la clé à la session avec `ssh-agent` auquel il faut passer le chemin de celle-ci.
Typiquement: 

`ssh-add ~/.ssh/id_rsa`
