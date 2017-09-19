---
author: admin
title: Installation Fedora 6 sur Dell D800
comments: true
link: http://www.nchapon.org/blog/?p=35
date: "2006-12-09"
wordpress_id: 35
slug: installation-fedora-6-sur-dell-d800
category: 'Linux'
---

![Fedora](http://www.nchapon.org/blog/wp-content/uploads/2006/12/fedoralogo-224x80.miniature.jpg)

J'ai récemment installé la [Fedora Core 6](http://www.fedoraproject.org) sur mon ordinateur portable du boulot (**Dell Latitude D800**), tout  s'est bien  passé sauf pour ma carte Wifi _ipw2100_ qui a bien été reconnue mais impossible de la faire fonctionner tout simplement parce que la mauvaise version du kernel est installée par Anaconda ! ([http://fedoraproject.org/wiki/Bugs/FC6Common](http://fedoraproject.org/wiki/Bugs/FC6Common))

Voici donc les manipulations que j'ai du effectuer pour faire fonctionner ma carte Wifi :

**1.** Il faut tout d'abord récupèrer les drivers de la carte Wifi avec Yum :

_**yum install ipw2100-firmware**_

**2.** Puis  verifier que le kernel installé est bien**_ kernel.i686_** en lançant la commande :

_**yum list kernel***_

Si ce n'est pas le cas il va falloir mettre à jour le kernel (avant cette étape il est préférable de sauvergarder le fichier de configuration de grub _/etc/grub.conf_).
**3.** Désinstaller le kernel avec la commande :

_**yum remove kernel**_

Cette commande supprime également d'autre packages qui seront réinstallés plus tard ...
**4.** Réinstaller la version du kernel correspondant à  l'architecture i686 avec :

_**yum install kernel.i686**_

**5.** Puis pour réinstaller les packages supprimés :

_**yum install gnome-session compiz gnome-volume-manager pcmciautils**_

Une fois que tout est installé il faut vérifier la conf de grub pour la faire pointer vers la bonne version du kernel et éffectuer un _reboot_ et normalement la carte Wifi devrait être opérationnelle.

Comme d'habitude avec cette distribution, il est parfois nécèssaire de mettre les mains dans le cambouis, mais hormis ce petit souci et le fait qu'elle n'embarque pas [firefox 2](http://www.mozilla-europe.org/fr/), cette distribution est vraiment très complète et particulièrement productive notamment pour le développement Java avec la dernière version d'[Eclipse](http://sources.redhat.com/eclipse/) estampillée Fedora .
Pour _firefox 2_, avant la release officielle Fedora, il est possible de le récupèrer _via _yum_ depuis le [dépot de Rémi Collet](http://remi.collet.free.fr/index.php?2005/10/02/8-telechargement-installation-et-yum)._
