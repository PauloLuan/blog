---
author: pauloluan
comments: true
date: 2012-08-26 18:03:14
layout: post
slug: gerar-chaves-ssh-linux
title: Gerar chaves SSH Linux
wordpress_id: 717
tags:
- GIT
- hub
- linux
- privada
- publica
- ssh
- ubuntu
---

Abra o terminal e digite >>>
    
    ``` bash
    ssh-keygen -t rsa
    sudo apt-get install xclip
    cat ~/.ssh/id_rsa.pub | xclip -sel clip
     
    ```
    
    Att,
    Paulo Luan
