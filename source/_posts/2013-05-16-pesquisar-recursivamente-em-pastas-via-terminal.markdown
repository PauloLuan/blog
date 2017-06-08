---
layout: post
title: "Pesquisar recursivamente em pastas via terminal"
date: 2013-05-16 10:46
comments: true
categories: 
---

comando:

``` bash
     grep -R "o que eu quero pesquisar" path_da_sua_pasta
```
<!-- more --> 

exemplo:
     
``` bash
     grep -R "texto de exemplo" ~/Documents
     grep -R "<html>ele também procura em arquivos de textos por qualquer tipo!</html>" source/
     grep -R "pode ser um texto em txt, um doc, enfim, ele vai achar..." source/
```