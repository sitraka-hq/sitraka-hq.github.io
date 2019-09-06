---
layout: post
title: Installer RVM sur Ubuntu 18.04.3 LTS
categories: ruby
comments: true
---

[RVM](https://rvm.io/) est un outil de ligne de commande qui vous permet d'installer, de gérer et de travailler facilement avec plusieurs environnements Ruby, des interpréteurs aux ensembles de gems.

[RVM](https://rvm.io/) a un paquet dédié pour Ubuntu que nous allons utiliser pour notre installation.

## Conditions préalables

Vous devez avoir installé préalablement software-properties-common pour pouvoir ajouter des dépôts PPA. Si ce n'est pas le cas, ouvrez un terminal `(Ctrl + Alt + T)` et exécutez:

```bash
$sudo apt install software-properties-common
```

## Ajouter le PPA et installer le paquet

Ouvrez un terminal `(Ctrl + Alt + T)` et exécutez:

```bash
$sudo apt-add-repository -y ppa:rael-gc/rvm
$sudo apt update
$sudo apt install rvm
```

## Changer votre fenêtre de terminal

Maintenant, afin de toujours charger rvm, changez le terminal Gnome pour toujours effectuer une connexion.

Dans la fenêtre du terminal, cliquez sur `Edition> Préférences de profil`, cliquez sur l'onglet `Titre et commande`, puis cochez la commande `Exécuter en tant que shell de connexion`.

## Redémarrer

De nombreuses modifications ont été apportés (scripts à recharger, vous êtes maintenant membre de rvm group) et, pour que tout fonctionne correctement, vous devez redémarrer (dans la plupart des cas, une déconnexion / connexion suffit, mais certains dérivés d’Ubuntu ou certains émulateurs de terminal, un login shell n’est pas effectué, nous vous conseillons donc de redémarrer).

## Utilisation

* Installer une version de ruby: `rvm install 2.4`
* Utiliser une version de ruby: `rvm install 2.4`
* Lister les version de ruby installées: `rvm list known`

## Conclusion

Pour conclure, RVM facilite l'utilisation de plusieuris versions de ruby sur un système d'exploitation.
 
