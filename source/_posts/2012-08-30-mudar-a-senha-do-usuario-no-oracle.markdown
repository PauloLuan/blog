---
author: pauloluan
comments: true
date: 2012-08-30 18:08:26
layout: post
slug: mudar-a-senha-do-usuario-no-oracle
title: Mudar a senha do usuário no Oracle
wordpress_id: 704
categories:
- Banco de Dados
tags:
- banco
- BD
- dados
- Oracle
---

Abra o cmd e digite:

Path default no Windows da instalação é o "C:oraclexeapporacleproduct11.2.0serverbin"

``` bash
sqlplus / as sysdba
alter user identified by
```


Exemplo:
``` sql
alter user system identified by root
```

