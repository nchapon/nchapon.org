---
author: admin
title: "Gestion des dépendances transitives avec Maven"
comments: true
link: http://www.nchapon.org/blog/?p=57
date: "2007-03-28"
wordpress_id: 57
slug: gestion-des-dependances-transitives-avec-maven
category: 'Java'
---

Le mécanisme de gestion transitive des dépendances de [Maven](http://maven.apache.org/) peut parfois engendrer des comportements inattendus ...
Dans un projet web, j'ai rencontré récemment un problème lors de l'utilisation conjointe des API [MyFaces](http://myfaces.apache.org/) (JSF) et [commons-logging](http://jakarta.apache.org/commons/logging/) (gestion des traces).

Le graphe des dépendances de l'application web est du type :

![Graphique](http://www.nchapon.org/blog/wp-content/uploads/2007/03/graph.png)
Le projet Maven **webapp-1.0.war** déclare deux dépendances explicites vers **projet-1.0.jar** et **myfaces-impl-1.1.5.jar**.

La version **1.1** de **commons-logging** est récupérée par transitivité et possède une dépendance implicite vers l'API [log4J ](http://logging.apache.org/log4j/docs/)ce qui permet d'afficher les traces via cette API.

Le problème c'est que l'API **myfaces-impl** a également une dépendance transitive vers **commons-logging** mais en version **1.0.4** or dans cette version la dépendance vers log4J est optionnelle, donc l'affichage des traces via log4J ne fonctionne plus, c'est le mécanisme de gestion des traces JDK qui s'en charge ...

Pour contourner ce problème, deux solutions :




  * Ajouter une exclusion de l'API **commons-logging** au niveau des dépendances _MyFaces_.


  * Déclarer explicitement la dépendance vers **commons-logging** dans la webapp de façon à  ne plus récupérer cette dépendance de manière transitive.


La deuxième solution est préconisée ([cf release notes Maven 2.0.5](http://maven.apache.org/release-notes.html)) : toutes les dépendances de compilation doivent être déclarées explicitement dans chaque projet même si celles-ci sont accessibles par transitivité.
