---
author: admin
title: Maven Dependency Plugin
comments: true
link: http://www.nchapon.org/blog/?p=73
date: "2008-06-19"
wordpress_id: 73
slug: maven-dependency-plugin
category: 'Java'
---

Avec [Maven 2](http://maven.apache.org/), la transitivité peut compliquer la gestion des dépendances et entrainer parfois des conflits dans la version des librairies récupérées de manière transitive et celles réellement déclarées dans le fichier _pom.xml_.

Bien que Maven fournisse un mécanisme permettant de résoudre ces conflits, il est parfois utile de contrôler les dépendances de notre projet, le plugin [maven-dependency-plugin](http://maven.apache.org/plugins/maven-dependency-plugin/index.html) permet d'effectuer cette tâche.

Tout d'abord, la commande suivante va permettre d'afficher l'arbre des dépendances avec leur _scope_ :
[code]mvn dependency:tree[/code]

Pour analyser les dépendances utilisées ou non par notre projet :
[code]mvn dependency:analyze[/code]

Cette commande est bien utile car par défaut elle permet de visualiser les dépendances utilisées mais non déclarées ainsi que les dépendances non utilisées mais déclarées dans le pom.xml.

On rappellera qu'il est préférable avec Maven 2 de déclarer toutes les dépendances nécessaires à la compilation au niveau de notre projet plutôt que de les récupérer par transitivité.

La transitivité doit se limiter aux dépendances runtime...
