---
layout: post
title: "Pesquisar por comandos digitados no terminal"
date: 2013-05-16 10:46
comments: true
categories: 
---

Aprenda a recuperar comandos que você já digitou anteriormente no terminal.

<!-- more -->

comando:

``` bash
   history | grep comando_que_você_digitou anteriormente
```

por exemplo:

``` bash
   history | grep commit
   history | grep scp
   history | grep cd
```