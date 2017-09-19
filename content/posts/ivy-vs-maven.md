---
author: admin
title: Maven vs Ivy
comments: true
link: http://www.nchapon.org/blog/?p=25
date: "2006-09-25"
wordpress_id: 25
slug: ivy-vs-maven
category: 'Java'
---

Sur le projet sur lequel je travaille actuellement, l'outil [Ivy](http://jayasoft.org/ivy) est utilisé à  partir de [Ant](http://ant.apache.org/) pour la construction et la génération des livrables (EAR et WAR).

Utilisant [Maven](http://maven.apache.org/) depuis plus de deux ans, je ne connaissais pas cet outil de build qui me semble intéressant pour les personnes ne voulant pas franchir le pas Maven et conserver leurs scripts Ant.

En gros Ivy est un outil open source qui est utilisé principalement pour la gestion des dépendances, on définit  les dépendances dans un fichier **_ivy.xml_** pour chaque projet Java, et Ivy va récuperer à  partir d'un script Ant les dépendances depuis le repository partagé de votre projet.

Au niveau des caractéristiques :




  * Ivy permet la gestion des dépendances de manière transitive (fonctionnalité dans Maven 2 uniquement),


  * On peut l'utiliser avec [Cruise Control ](http://cruisecontrol.sourceforge.net/)pour mettre en place une plate-forme de build continu


  * il existe un [repository Ivy officiel ](http://ivyrep.jayasoft.org/content.html)sur le web (un peu comme le [repository Maven](http://www.ibiblio.org/maven2/) mais ne contenant que les fichiers ivy.xml, il est d'ailleurs conseillé d'aller chercher ces fichiers sur le repo Maven)


  * enfin, il existe un [plugin Ivy](http://www.jayasoft.org/ivyde) pour [eclipse](http://www.eclipse.org) permettant par exemple de redescendre la dernière version d'un Jar dans l'environnement de développement


Maintenant, après quelques mois d'utilisation (j'ai eu beau parlé de Maven à  mon client, il ne veut rien savoir), je dois dire que l'équipe en place depuis deux ans maà®trise plutà´t bien son build, (une centaine de projets Java avec compilation AspectJ) mais à  quel prix : il y a **10000** lignes de script ant pour compiler **400000** lignes de code Java !

Vous l'aurez compris le point noir d'Ivy c'est qu'il ne permet pas de s'affranchir de scripts Ant, dans le cas de gros projets le choix d' Ivy par rapport à  Maven n'est donc pas très conseillé. Je limiterai donc l'utilisation de cet outil dans le cadre de petits projets, pour les gens qui ne veulent pas passer à  Maven ou ne veulent pas tout simplement investir du temps sur la prise en main de Maven.

Pour les sceptiques qui hésiteraient encore entre Maven et Ivy :
_** Maven = Ant + Ivy + tout plein de plugins**_

Pour moi, il n'y a pas photo Maven est actuellement l'outil de build le plus performant.
