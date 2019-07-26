---
layout: post
title: Faciliter le développement de paquet NPM
categories: [NodeJs, npm]
comments: true
---

Nous allons voir dans cet article comment faciliter le développement d’un paquet NPM en utilisant la commande `npm link`. Cette commande permet de créer [un lien symbolique](https://fr.wikipedia.org/wiki/Lien_symbolique) du paquet en cours de développement vers le paquet ou l'application qui va l'utiliser.

## Présentation de la commande `npm link`

Supposons que nous ayons un paquet que l’on souhaite développer parallèlement avec une application qui l’utilise. Il existe plusieurs façons de faire:
* Copier/coller le paquet dans le répertoire node_modules ce qui est trop répétitif.
* Utiliser git submodule ceux rend le processus de développement plus complexe.

La meilleure solution est d’utiliser `npm link`. Cette commande permet de créer un lien symbolique du paquet que l’on va créer vers le répertoire `node_modules` de l’application qui va l’utiliser. Ainsi on peut séparer l’application et le paquet que l’on  souhaite utiliser sur l’application dans deux (02) répertoires différents. Cela permet aussi d’utiliser git (sans utiliser les sous modules) sur le paquet qu’on va créer et sur l’application.

## Utilisation de la commande `npm link`

Nous allons voir ici comment utiliser la commande `npm link`. Dans un premier temps, nous allons créer un module qui permet d’afficher « Bonjour ! » sur la console. Ensuite, nous créerons une application qui utilisera le paquet que nous avons créé afin d’afficher le message « Bonjour ! » sur la console.

Commençons par placer notre module dans un répertoire que l'on va appeler bonjour.
```sh
$mkdir bonjour
$cd bonjour
$touch index.js
$npm init
```
`npm init` permet d’initialiser un paquet npm. Cette commande génere un fichier `package.json` qui contiendra tous les informations sur le paquet (l’auteur, le nom, la description, les dépendances…).
Maintenant, créons la fonction qui dit bonjour dans le fichier `index.js` :
```js
module.exports = "bonjour!"
```
Ensuite, nous allons créer l’application qui l’utilisera:
```sh
Cd ..
mkdir bonjour-app
cd bonjour-app
touch index.js
npm init
```
Dans le fichier index nous allons utiliser le module `bonjour` :
```js
const bonjour = require('bonjour');
console.log(bonjour);
```

Créons maintenant un lien symbolique du paquet vers l’application qui l’utilisera. Pour le faire, tout d’abord, il suffit juste de tapez `npm link` dans le répertoire racine du paquet qui affiche bonjour. Puis dans le répertoire de l’application qui va l’utiliser, il suffit d’entrer la commande `npm link bonjour` où «bonjour » est le nom du paquet que nous avons précédemment créé.

> Pour utiliser `npm link` il est nécessaire que les modules ayent un fichier `package.json` valide.

> La commande `npm link` peut bien être utilisé sur tous les systèmes d'exploitation même si les systèmes d'exploitation Windows ne supportent pas nativement les liens symboliques.

## Conclusion

`npm link` est disponible sur toutes les versions de NPM. La commande permet `npm link` permet de faciliter considérablement le processus de développement de paquet car elle est très simple à utiliser.
J’espère que cet article vous a aidé. N’hésitez pas à laisser un commentaire.
Dans un prochain article je vais vous montrez comment publier un paquet sur le dépôt de NPM.
