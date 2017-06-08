---
author: pauloluan
comments: true
date: 2012-09-04 14:19:03
layout: post
slug: configurando-java_home-no-mac
title: Configurando JAVA_HOME no Mac
wordpress_id: 754
categories:
- Metodologias
tags:
- ambiente
- home
- java
- mac
- variavel
---

Digite no Terminal:

``` bash
sudo su
vim ~/.bash_profile
```

Adicione ao final do arquivo

``` sql
export JAVA_HOME=`/usr/libexec/java_home -v 1.6`
```

Pressione Esc digite :wq
(W de Write e Q de Quit)

Pronto!
