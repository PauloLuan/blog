---
layout: post
title: "Introdução ao RingoJS - Aplicações WEB com Javascript Server Side"
date: 2013-10-28 16:07
comments: true
categories: ["js", "javascript"]
---

RingoJS 

Ringo is a CommonJS-based JavaScript runtime written in Java and based on the Mozilla Rhino JavaScript engine. It takes a pragmatical and non-dogmatic stance on things like I/O paradigms. Blocking and asynchronous I/O both have their strengths and weaknesses in different areas.

<!-- more -->
http://ringojs.org/
http://ringojs.org/documentation/


```  bash Clone o repositório
git clone https://github.com/ringo/ringojs.git
cd ringojs/
```

``` bash Execute este comando para ver as possíveis funções a serem executadas.
ant
```

``` bash Compilando o Ringo.
ant update && ant jar && ant compile
```

``` bash Execute o Modo iterativo
./bin/ringo
```

``` bash 
nano ~/.bashrc # linux
nano ~/.bash_profile # mac
```

``` bash Adicione na última linha do arquivo os executáveis
export PATH="$PATH:<SEU_PATH_AQUI>"

exemplo:

export PATH="$PATH:/Users/funcatemobile/Desktop/jug-ringo/ringojs/bin/"
```

Aperte CTRL + X para salvar e sair.


```  bash Imprimindo um arquivo de texto
var fs = require('fs');
var file = fs.read('teste.txt');
print(file);
```


``` bash Criando app com o ringo-admin
./ringojs/bin/ringo-admin create jug-teste
cd jug-teste
tree
../ringojs/bin/ringo main.js
```

``` bash Clonando o repositório com o template do maven.
git clone https://github.com/PauloLuan/ringo-maven.git
ant
mvn clean install
```

``` bash Colocando em produção no Tomcat
cp target/ringo-maven.war ~/Documents/Desenvolvimento/Tomcat/apache-tomcat-7.0.32/webapps/
```

``` bash Módulo de autenticação Social utilizando um projeto Java.
git clone https://github.com/PauloLuan/ringo-socialauth.git
```


``` bash Crud com MongoDB usando Java Driver!
git clone https://github.com/PauloLuan/ringo-mongodb.git
```

``` bash 
Baixe os Slides: https://gist.github.com/PauloLuan/7123760
```