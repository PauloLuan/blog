---
author: pauloluan
comments: true
date: 2012-03-28 11:48:04
layout: post
slug: nginx-como-listar-suas-pastas-autoindex-na-pagina-inicial
title: Nginx - Como Listar suas pastas (AutoIndex) na página inicial.
wordpress_id: 586
categories:
- Metodologias
---

O Nginx por default não lista as pastas do seus projetos que ficam em (/usr/share/nginx/www/), por exemplo, se você tiver apenas pastas com os seus projetos sem nenhuma página inicial o Nginx lançará um erro 403 pois não encontrará uma página inicial para acessar e não listará as pastas que existem neste diretório. Para solucionar este problema, modifique o arquivo de configurações do seu Nginx com o seguinte comando:

<!-- more -->

``` bash sudo gedit /etc/nginx/sites-available/default ```

Vai ser algo parecido com isto o seu arquivo:

``` bash
server {
	listen   83; ## listen for ipv4; this line is default and implied
	#listen   [::]:80 default ipv6only=on; ## listen for ipv6

	root /usr/share/nginx/www;
	index index.html index.htm;

	# Make site accessible from http://localhost/
	server_name localhost;

	location / {
		# First attempt to serve request as file, then
		# as directory, then fall back to index.html
		try_files $uri $uri/ /index.html;
	}

	location /doc {
		root /usr/share;
		autoindex on;
		allow 127.0.0.1;
		deny all;
	}

	location /images {
		root /usr/share;
		autoindex off;
	}```

Devemos alterar apenas a Tag "location/ { ... }" adicionando o atributo "autoindex on" ficando assim:

``` bash
location / {
        autoindex on;
	# First attempt to serve request as file, then
	# as directory, then fall back to index.html
	try_files $uri $uri/ /index.html;
}```




    
    Reinicie o servidor:




``` bash sudo /etc/init.d/nginx restart```

Comando útil para poder editar os arquivos do projeto:

``` bash sudo chmod -R 777 /usr/share/nginx/www/```





 Att,




Paulo Luan






