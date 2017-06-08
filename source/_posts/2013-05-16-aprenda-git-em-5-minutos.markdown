---
layout: post
title: "Aprenda GIT em 5 minutos! "
date: 2013-05-16 11:20
comments: true
categories: ["git"]
---

Guia de sobrevivência para aprender git em alguns passos bem rápidos.

<!-- more -->

Linux:

``` bash Instale o GIT via apt-get
     sudo apt-get install git # Linux
``` 

configure para que a cada commit que você fizer fique com seu nome e email:

``` bash
     git config --global user.name "SEU NOME AQUI"
     git config --global user.email "seuemail@example.com"
```
clonando um repositório remoto (cópia do repositório remoto na sua máquina).

``` bash
     git clone url_do_repositorio
```

exemplo:

``` bash
     git clone https://github.com/PauloLuan/ProjetosPoliticosSJC.git # cópia do repositório remoto na sua máquina
```
para commitar e enviar para o servidor:

``` bash
     git add . # adiciona todos os arquivos para serem commitados
     git commit -a -m "mensagem de seu commit" # faz um novo commit das suas modificações
     git push origin master # envia pro servidor as modificações
```

Receber modificações do repositório remoto, caso alguém tenha commitado algo:

``` bash
    git pull
```

Quer saber tudo de GIT? Leia os tutoriais e livros abaixo!

1 - [livro ProGIT](http://git-scm.com/book/pt-br) gratuito, e em Pt-BR.

2 - [learnGitBranching](http://pcottle.github.io/learnGitBranching/)

3 - [Aprendendo Git Sem Complicações](http://rogerdudler.github.io/git-guide/index.pt_BR.html)