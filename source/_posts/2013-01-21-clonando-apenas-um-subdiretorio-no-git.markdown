---
author: pauloluan
comments: true
date: 2013-01-21 09:42:10
layout: post
slug: clonando-apenas-um-subdiretorio-no-git
title: Clonando apenas um subdiretório no GIT
wordpress_id: 346
categories:
- Metodologias
tags:
- apenas
- clonando
- folder
- GIT
- only
- pasta
- submodules
---
``` bash
git clone < URL DO REPOSITÓRIO >
cd < DIRETÓRIO >
git config core.sparsecheckout true
echo <NOME DA PASTA QUE VOCÊ QUER> >> .git/info/sparse-checkout
git read-tree -m -u HEAD
```
<!-- more --> 

[Fonte](http://eminetto.github.com/blog/2012/04/25/git-sparse-checkouts/)
