---
author: admin
title: "Gérer ses notes avec Zim"
comments: true
link: http://www.nchapon.org/blog/?p=136
date: "2011-05-09"
wordpress_id: 136
slug: gerer-ses-notes-avec-zim
categories:
  - 'Bazar'
  - 'Linux'
---

Pour gérer mes notes personnelles cela fait quelques mois que j'ai abandonné  [Gnote](http://live.gnome.org/Gnote) au profit de [Zim](http://zim-wiki.org/).
Zim est un "wiki de bureau" qui permet de gérer et d'organiser ses notes personnelles ou ses listes de tâches dans un wiki, il fonctionne sur Linux, Mac et Windows. (Cf fiche Zim sur le site [framasoft](http://www.framasoft.net/article5076.html))

En général, j'utilise Zim en mode nomade, à partir d'un disque USB pour stocker le contenu des notes (fichiers textes avec balises wiki) et j'utilise un outil de versionning pour synchroniser mes notes avec mon PC personnel ou celui du travail (par défaut Zim fournit un plugin pour s'interfacer avec [Bazaar](http://bazaar.canonical.com/en/) mais dans mon cas je préfère utiliser [Git](http://git-scm.com/)).

L'installation de Zim est relativement simple, des binaires compilés sont disponibles sur la plupart des grandes distributions Linux.
Avec Fedora, on installe Zim en utilisant _yum_ :

`yum install zim`

Pour les utilisateurs Windows, il est possible que Zim refuse de se lancer, cela provient en général d'une _DLL_ manquante. Il est possible de résoudre ce problème en récuperant la DLL  **msvcr90.dll** (fournie avec Python 2.6.X) et de la recopier dans le répertoire d'installation de Zim.

Enjoy ;-)
