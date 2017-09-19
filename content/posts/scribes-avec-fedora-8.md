---
author: admin
title: Scribes avec Fedora 8
comments: true
link: http://www.nchapon.org/blog/?p=67
date: "2008-03-07"
wordpress_id: 67
slug: scribes-avec-fedora-8
category: 'Linux'
---

![scribes.png](http://www.nchapon.org/blog/wp-content/uploads/2008/03/scribes.png) [Scribes](http://scribes.sourceforge.net/) est un petit éditeur de texte _Open Source_ écrit en [Python](http://www.python.org/) qui fonctionne sous **Gnome**. Cet éditeur est vraiment très sympathique à utiliser, il reprend les concepts du fameux éditeur de texte [TextMate](http://macromates.com/) qui tourne sur _Mac OS X_.

Pour installer scribes depuis les sources il faudra d'abord s'assurer que les bindings python GTK2 sont bien présents, dans mon cas j'ai eu besoin de récupérer avec **yum** les paquets suivants :


[code]
yum install gnome-python2-gtksourceview gnome-python2-gtkspell
[/code]


Puis l'installation s'effectue à  partir des fichiers sources de la façon suivante :


[code]
tar xjf scribes-0.3.3.3.tar.bz2
cd scribes-0.3.3.3
./configure
make
sudo make install
-
[/code]


Puis lancer scribes depuis le menu Gnome _Applications > Accessoires > Scribes Text Editor_.
