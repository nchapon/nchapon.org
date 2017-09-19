---
author: admin
title: XFire vs Axis2 vs JAX-WS
comments: true
link: http://www.nchapon.org/blog/?p=42
date: "2007-02-11"
wordpress_id: 42
slug: xfire-vs-axis2-vs-jax-ws
category: 'Java'
---

![xfire.png](http://www.nchapon.org/blog/wp-content/uploads/2007/02/xfire.miniature.png) _**VS**_ ![axis.jpg](http://www.nchapon.org/blog/wp-content/uploads/2007/02/axis.miniature.jpg) _**VS**_ ![glassfish_logo.gif](http://www.nchapon.org/blog/wp-content/uploads/2007/02/glassfish_logo.gif)
Si vous hésitez sur le choix de la technologie à  adopter pour implémenter vos [services web](http://fr.wikipedia.org/wiki/Web_service), deux nouveaux benchs récents pour tenter de vous éclairer :




  * [WS Oxygen Tank](http://www.wso2.com/) (_**société qui fournit un framework basé sur [Axis2](http://ws.apache.org/axis2/index.html)**_) propose une [confrontation entre Axis2 et XFire](http://wso2.org/library/588) et c'est Axis2 (avec **ADB** pour le binding XML) qui semble plus rapide que [XFire](http://xfire.codehaus.org/) ...




  * Le [deuxième bench](http://weblogs.java.net/blog/kohsuke/archive/2007/02/jaxws_ri_21_ben.html), **_réalisé par des développeurs de Sun_**, oppose la dernière version de [JAX-WS](https://jax-ws.dev.java.net/2.1/) (solution de Sun pour l'implémentation de services web) à  _**Axis2 **_et il semble que _**JAX-WS**_ soit la solution la plus performante ...


On le voit clairement ces deux benchs n'ont pas été réalisés dans les meilleurs conditions d'impartialité, comme par hasard dans les deux benchs, le binding avec [JiBX](http://jibx.sourceforge.net/) n'a pas été testé que ce soit avec **_XFire_** pour le permier bench ou _**Axis2**_ pour le second.
Aujourd'hui les trois principales implémentations Java de services web semblent avoir des performances comparables, le choix s'oriente donc plus vers les fonctionnalités, le respect des normes (qui ne sont pas encore toutes standardisées) et surtout la facilité d'implémentation et de mise en place.

Au cours d'une mission j'ai assisté à  des tests de performances entre **_Axis 2_** (avec binding **_ADB_**) et _**XFire**_ (avec binding par défaut _**Aegis**_), nous avons obtenu des résultats comparables, sauf que pour **_Axis2_** nous avons eu des problèmes d'accès concurrents lors des montées en charge (apparemment les testeurs de Sun on eu les mêmes soucis).

Nous avons choisi d'utiliser **_XFire_** pour sa simplicité (intégration avec [Spring](http://www.springframework.org/), gestion des dépendances depuis [Maven ](http://maven.apache.org/)...) et ses très bonnes performances, à  coté _**Axis2**_ apparait comme une belle _usine à  gaz_ ...

En ce qui concerne **_JAX-WS_** cette solution semble prometteuse, c'est la solution qui respecte le plus les nouveaux standards, mais elle est encore beaucoup trop estampillée _Sun_, elle ne fournit qu'un seul _data binding_ [JAXB2](https://jaxb.dev.java.net/).
