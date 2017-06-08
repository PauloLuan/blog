---
author: pauloluan
comments: true
date: 2012-08-26 15:48:28
layout: post
slug: comecando-com-nosql-mongodb-pymongo
title: Começando com NoSQL - MongoDB + PyMongo
wordpress_id: 699
categories:
- Banco de Dados
tags:
- banco
- dados
- db
- mongo
- nosql
- python. mongodb
- sql
---

Este tutorial foi realizado no sistema operacional Ubuntu 12.04, mas os comandos são parecidos em todas as plataformas.

Para começar acesse o site oficial e faça o download dos binários para sua plataforma:

[http://www.mongodb.org/downloads](http://www.mongodb.org/downloads)

Logo em seguida, descompacte o conteúdo do arquivo mongodb-linux-x86_64-2.0.7.tgz em uma pasta qualquer que no meu caso é a

``` bash /home//Desenvolvimento/mongo ```

<!-- more -->



Em seguida crie uma pasta necessária para o funcionamento do MongoDB:

``` bash

sudo mkdir /data

cd /data

sudo mkdir db

```

Para iniciar o seu banco de dados acesse o terminal apertando CTRL+ALT+T digite o comando

``` bash cd ~/Desenvolvimento/mongo/mongodb-linux-x86_64-2.0.7/bin ```

(este ~ é equivalente a /home/<NOME DE SEU USUARIO>/) logo depois, digite

``` bash sudo ./mongod ```

abra outro terminal digitando

``` bash
cd ~/Desenvolvimento/mongo/mongodb-linux-x86_64-2.0.7/bin

mongo
```

se aparecer algo como isto:

[![](http://javalees.files.wordpress.com/2012/08/mongo-funcionando.png)](http://javalees.files.wordpress.com/2012/08/mongo-funcionando.png)

parabéns você conseguiu instalar! rs

Instalando o PyMongo:

Acesse a página oficial neste link: [https://github.com/mongodb/mongo-python-driver](https://github.com/mongodb/mongo-python-driver)

Comandos utlizados:

``` bash
sudo su

apt-get install build-essential python-dev

apt-get install git

cd ~/

git clone git://github.com/mongodb/mongo-python-driver.git pymongo

cd pymongo/

python setup.py install
```

Instalado!! agora vamos brincar um pouco com o mongoDB no Python:

digite na linha de comando:

``` bash
>>> python
>>> import pymongo
>>> connection = pymongo.Connection("localhost", 27017)
>>> db = connection.test
>>> db.name
u'test'
>>> db.my_collection
Collection(Database(Connection('localhost', 27017), u'test'), u'my_collection')
>>> db.my_collection.save({"x": 10})
ObjectId('4aba15ebe23f6b53b0000000')
>>> db.my_collection.save({"x": 8})
ObjectId('4aba160ee23f6b543e000000')
>>> db.my_collection.save({"x": 11})
ObjectId('4aba160ee23f6b543e000002')
>>> db.my_collection.find_one()
{u'x': 10, u'_id': ObjectId('4aba15ebe23f6b53b0000000')}
>>> for item in db.my_collection.find():
...     print item["x"]
...
10
8
11
>>> db.my_collection.create_index("x")
u'x_1'
>>> for item in db.my_collection.find().sort("x", pymongo.ASCENDING):
...     print item["x"]
...
8
10
11
>>> [item["x"] for item in db.my_collection.find().limit(2).skip(1)]
[8, 11]
```



``` bash >>> [item["x"] for item in db.my_collection.find().limit(2).skip(1)] ```

Nesta página você pode conferir todos os releases das documentações do MongoDB, na data deste post o último release é o [http://downloads.mongodb.org/docs/mongodb-docs-2012-08-26.pdf](http://downloads.mongodb.org/docs/mongodb-docs-2012-08-26.pdf) o legal é que dá pra baixar o PDF para futuras consultas sem a necessidade de internet.

Para iniciarmos com mongoDB existe um Shell interessantíssimo do qual você pode utilizar os comandos e ver como funcionam os CRUDs (Inserção, Remoção e Atualização) básicos no Mongo, para isto clique em “Try It Now” na página oficial [http://www.mongodb.org/](http://www.mongodb.org/).

Um caso interessante de sucesso na implementação do MongoDB é o CartolaFC da Globo.com, confira o artigo na integra neste link: [http://www.gonow.com.br/blog/2011/07/29/o-mongodb-aplicado-ao-cartolafc-da-globo-com/](http://www.gonow.com.br/blog/2011/07/29/o-mongodb-aplicado-ao-cartolafc-da-globo-com/)

Parabéns! Agora você pode incluir no currículo que mexeu com MongoDB! :D

Abraços!

Paulo Luan.

pesquisas futuras:

[http://www.tornadoweb.org/](http://www.tornadoweb.org/)

[https://github.com/bitly/asyncmongo](https://github.com/bitly/asyncmongo)
