---
layout: post
title: "Enviando chaves ssh para o servidor remoto com apenas um comando"
date: 2013-05-16 10:22
comments: true
categories: 
---

Gere chaves SSH da sua máquina e envie para o servidor remoto com o seguinte comando:

``` bash Comando: 
    ssh-keygen -t rsa && cat ~/.ssh/id_rsa.pub | ssh <user>@<hostname> 'cat >> ~/.ssh/authorized_keys'
``` 