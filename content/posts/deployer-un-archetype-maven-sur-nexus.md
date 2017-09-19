---
author: admin
title: Deployer un archetype Maven sur Nexus
comments: true
link: http://www.nchapon.org/blog/?p=145
date: "2011-06-29"
wordpress_id: 145
slug: deployer-un-archetype-maven-sur-nexus
categories:
  - 'Java'
  - 'Maven'
---

L'utilisation d'archétype Maven est bien utile pour permettre de créer un squelette de projet Java embarquant un minimum de code et définissant un jeu de dépendances.
Pour se faire une petite idée en lançant la commande `mvn archetype:generate` il y a plus de 100 archetypes de projets disponibles.
Ces archetypes de projets (open source) sont publiés sur  le [repository maven](http://search.maven.org/#browse) public sur internet.

Dans le cas de développement en entreprise, il peut être également très intéressant de développer des archétypes pour simplifier le démarrage des projets en fournissant par exemple le code Java de fonctionnalités réutilisables (connexion à un annuaire LDAP etc...).

Pour que cet archétype soit accessible par les équipes de développement et comme il n'est pas envisageable de le déployer sur le repository Maven public il est conseillé de le déployer sur le proxy Maven de l'entreprise par exemple sur [Nexus](http://nexus.sonatype.org/).

Tout d'abord avant de déployer un archétype il faut créer un archétype depuis un projet Maven existant.
Pour cela Maven nous facilite la tâche en utilisant la commande suivante :



    mvn archetype:create-from-project



_Astuce : attention aux fichiers générés par eclipse, donc le mieux c'est de faire ces opérations depuis un checkout de votre outil de gestion de configuration préféré_.

Se déplacer dans le répertoire créé


    cd target/generated-sources/archetype


Puis installer l'archétype en local :


    mvn install



Il est alors possible de tester l'archetype en local


    mvn archetype:generate -DarchetypeCatalog=local



Puis si le résultat est correct on peut deployer l'archetype sur Nexus en lançant la commande :


    mvn deploy



Par je ne sais quel mystère, mais dans mon cas avant de tester l'archetype il est nécessaire de créer un fichier **archetype-catalog.xml** et de le placer dans le répertoire _releases_ (ou _snapshot_) du serveur Nexus.
Dans ce fichier il faudra renseigner  les informations de l'archetype (groupId, artifactId, version et URL du repository)




    <?xml version="1.0" encoding="UTF-8"?>
    <archetype-catalog>
      <archetypes>
        <archetype>
          <groupId>com.mycompany</groupId>
          <artifactId>webfuse</artifactId>
          <version>1.3</version>
          <repository>http://sourceforge.mycompany.com:8081/nexus/content/repositories/releases</repository>
          <description>WebFuse Archetype</description>
        </archetype>
      </archetypes>
    </archetype-catalog>




Il est alors possible de tester l'archetype en lançant la commande :


    mvn archetype:generate -DarchetypeCatalog=http://sourceforge.mycompany.com:8081/nexus/content/repositories/releases
