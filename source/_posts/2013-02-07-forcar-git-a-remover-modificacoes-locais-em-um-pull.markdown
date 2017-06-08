---
author: pauloluan
comments: true
date: 2013-02-07 11:27:35
layout: post
slug: forcar-git-a-remover-modificacoes-locais-em-um-pull
title: Forçar git a remover modificações locais em um pull
wordpress_id: 801
tags:
- GIT
- locais
- modificações
- remover
---

``` bash
git fetch --all && git reset --hard origin/master
```

[fonte](http://stackoverflow.com/questions/1125968/force-git-to-overwrite-local-files-on-pull)
