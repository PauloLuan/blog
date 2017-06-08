---
layout: post
title: "Crie aplicações utilizando Gulp e faça deploy no Github gratuitamente."
date: 2015-04-29 12:46
comments: true
categories: [gulp, js, node, bower, yeoman, gh-pages, github]
---
{% img /images/gulp.png %}

Crie aplicações web estáticas seguindo as melhores práticas do mercado, e faça o deploy gratuitamente no Github através do GH-Pages

<!-- more -->


Vamos utilizar um [gerador](https://github.com/yeoman/generator-gulp-webapp) de estruturas de aplicações web do gulp, ele vai gerar um site estático com as melhores práticas utilizando [gulp](http://gulpjs.com/).

Vamos seguir o [Getting Started](https://github.com/yeoman/generator-gulp-webapp#getting-started) disposto na documentação do github:

Instale as dependencias globais (yeoman e bower): `npm install --global yo bower`

Instale o gerador: `npm install --global generator-gulp-webapp`

Digite `yo gulp-webapp` para criar o esqueleto da webapp.

Digite `gulp serve` para visualizar o site e ele automaticamente verifica se algum arquivo foi modificado e dispõe sem precisar reiniciar o servidor.

Digite `bower install --save <package>` para instalar as dependências para o frontend

Digite `gulp` para criar a aplicação pronta para o deploy, ele gera uma pasta chamada `dist` da qual terão todos os css e js minificados prontos para o deploy em produção.

Esta pasta `dist` você pode jogar em um servidor de sites estáticos como nginx ou apache, mas no meu caso eu queria usar o serviço do github-pages.

O github dispõe de um serviço chamado [Github-Pages](https://pages.github.com/) do qual você pode publicar sites estáticos (CSS, JS e HTML) de graça, é bom para que você possa publicar o front end no github pages e colocar sua API em algum outro servidor, perfeito pra usar com AngularJS por exemplo.

Para publicar essa pasta `dist` no gh-pages existe um [plugin](https://www.npmjs.com/package/gulp-gh-pages) que você adiciona como tarefa para que com um comando você consiga fazer o deploy automático.

Na pasta do projeto gerado digite: `npm install --save-dev gulp-gh-pages`

isso ira baixar a dependência e ainda modificar o arquivo `packages.json` automaticamente, de forma a deixar versionado corretamente as dependências da aplicação.

No arquivo `gulp.js` adicione o seguinte trecho:

{% codeblock lang:js %}
var ghPages = require('gulp-gh-pages');
 
gulp.task('deploy', function() {
  return gulp.src('./dist/**/*')
    .pipe(ghPages());
});
{% endcodeblock %}

Agora para fazer o deploy, basta digitar: `gulp deploy` e a pasta `dist` será publicada automaticamente no branch gh-pages.