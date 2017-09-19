---
author: admin
title: Artifactory
comments: true
link: http://www.nchapon.org/blog/?p=53
date: "2007-03-11"
wordpress_id: 53
slug: artifactory
category: 'Java'
---

[Artifactory](http://www.jfrog.org/sites/artifactory/latest/index.html) est un proxy [Maven 2](http://maven.apache.org) qui semble très prometteur, de part sa facilité d'installation et de configuration, et surtout par son mécanisme original de stockage du repository dans une base de données [derby](http://db.apache.org/derby/) Ã  partir de l'API Java [Jackrabbit](http://jackrabbit.apache.org). Ainsi, avec le stockage du repository en base de données il est possible rapidement d'effectuer des recherches et surtout les dépôts dans le repository peuvent être effectués de manière atomique au sein d'une transaction (un peu comme [subversion](http://subversion.tigris.org/)).

Pour installer **_artifactory_** il suffit de lancer le script **_install.sh_** pour démarrer une webapp via le moteur de servlet [Jetty](http://www.mortbay.org/) embarqué.

Puis on accède à  la console d'administration Ã  partir de l'URL **_http://localhost:8081/artifactory_** (un utilisateur _admin/password_ est créé par défaut).
