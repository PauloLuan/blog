---
layout: post
title: "Apt-get no Windows"
date: 2015-04-28 20:23
comments: true
categories: windows, cmd, apt-get, linux
---

{% img /images/chocolatey.png %}

Transforme o seu windows em um Linux-Like com o chocolatey, com ele você poderá instalar vários aplicativos através de um comando simples no terminal. Nunca mais instale o asktoolbar (ou hao123) por engano ;)

<!-- more -->

Abra o cmd com privilégios de administrador, e digite:

{% codeblock lang:bat %}
@powershell -NoProfile -ExecutionPolicy unrestricted -Command "iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))" && SET PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin
{% endcodeblock %}


Agora você pode instalar qualquer um dos pacotes disponíveis no site oficial. Para procurar os pacotes basta acessar o [site oficial](https://chocolatey.org/packages)  e procurar, você pode instalar o chrome (não precisa mais usar o internet explorer para isto), firefox, sumatrapdf, java, flash, nodejs, git, svn e muitos outros, tudo via choco install! 

para instalar o git por exemplo:

{% codeblock lang:bat %}
choco install git -y
{% endcodeblock %}

Ele vai instalar tudo automáticamente, a opção -y é para que ele instale sem perguntar nada, por default ele exibe o script que vai ser executado na sua máquina, pois todos os pacotes são feitos pela comunidade, logo, pode ser que dentro do script que será executado possa ter algum tipo de requisição que você não queria que seja executada, o que é muito raro, já que todos os pacotes passam por um processo de aprovação rígido pelos admins do projeto, o que por vezes gera certa lentidão na aprovação de um pacote no caso de você criar um.

Adicionalmente, as mesmas instruções estão no site do [chocolatey](https://chocolatey.org/).
