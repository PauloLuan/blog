---
author: pauloluan
comments: true
date: 2012-10-17 08:57:00
layout: post
slug: adicionando-tablespace-no-oracle
title: Adicionando Tablespace no Oracle
wordpress_id: 763
categories:
- Banco de Dados
tags:
- 10g
- 11g
- banco
- bancos
- dados
- datafile
- dataspace
- Oracle
- tablespace
---

Para adicionar mais espaço no Oracle digite o seguinte comando:

``` sql
ALTER TABLESPACE <Nome>
 ADD DATAFILE '<Caminho do local onde será salvo>' SIZE<tamanho em mb> M
 AUTOEXTEND ON;
```

Por Exemplo:

``` sql
ALTER TABLESPACE SYSTEM</div>
ADD DATAFILE 'E:OracleDBtarefa.dbf' SIZE 2000M
AUTOEXTEND ON;
```

Para verificar quanto espaço temos alocado basta digitar o comando:

--Espaço utilizado no BD

``` sql
select nvl(b.tablespace_name, nvl(a.tablespace_name,'UNKNOWN')) "Tablespace", kbytes_alloc "Allocated MB", kbytes_alloc-nvl(kbytes_free,0) "Used MB",
 nvl(kbytes_free,0) "Free MB", ((kbytes_alloc-nvl(kbytes_free,0))/kbytes_alloc) "Used", data_files "Data Files" from ( select sum(bytes)/1024/1024 Kbytes_free,
 max(bytes)/1024/1024 largest, tablespace_name from sys.dba_free_space group by tablespace_name ) a, ( select sum(bytes)/1024/1024 Kbytes_alloc, tablespace_name,
 count(*) data_files from sys.dba_data_files group by tablespace_name ) b where a.tablespace_name (+) = b.tablespace_name order by 1;
```
