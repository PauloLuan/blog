---
author: pauloluan
comments: true
date: 2012-01-16 12:18:43
layout: post
published: false
slug: como-criar-um-repositorio-svn-utilizando-google-code
title: Como criar um repositório SVN utilizando Google Code
wordpress_id: 125
categories:
- Você não pode morrer sem saber!
tags:
- code
- como
- create
- criar
- GIT
- google
- how
- java
- mercurial
- projeto
- repositório
- reposito
- repository
- SVN
- to
- trunk
- tutorial
---

Atenção: Se você nunca utilizou um sistema de controle de versões, leia este artigo! (Gostaria muito que alguém tivesse dito estas dicas quando iniciei minha faculdade, teria mudado minha vida! rs então utilizem este artigo para facilitar a sua vida! Haushaush Espero que minha experiência possa lhe ajudar ;) Se gostar agradeça nos comentários, aperte CTRL+ D e adicionem nosso blog aos seus favoritos! Hehe)

Este artigo tem como objetivo demonstrar de forma prática, como criar um repositório SVN no Google Code, além de mostrar diversas opções de Servidores que hospedam repositórios de controle de versão. Recomendo que leia antes deste tutorial ;) [O que é e como utilizar um sistema de controle de versão SVN](http://javalees.wordpress.com/2012/01/16/o-que-e-e-como-utilizar-um-sistema-de-controle-de-versao-svn/)

<!-- more -->

Para iniciar nosso tutorial vamos instalar o SVN no eclipse. A instalação do Plugin SVN pode ser realizada em qualquer versão do eclipse. (se ainda não tem o eclipse pode baixar [aqui](http://www.eclipse.org/downloads/))

Abra o eclipse, clique em help → Install new Software

[![](http://javalees.files.wordpress.com/2012/01/captura_de_tela-java-ee-eclipse.png)](http://javalees.files.wordpress.com/2012/01/captura_de_tela-java-ee-eclipse.png)

Nesta janela coloque o seguinte link: http://subclipse.tigris.org/update_1.6.x Selecione as três opções e concorde com os termos da instalação, clique em next → next (Reinicie o eclipse após a finalização da instalação).

[![](http://javalees.files.wordpress.com/2012/01/captura_de_tela-3.png)](http://javalees.files.wordpress.com/2012/01/captura_de_tela-3.png)

Criarei um projeto SVN no Google Code para demonstrar a criação do nosso projeto de testes (vocês poderão fazer o download do projeto pra testar ai no seu PC), a única desvantagem de postar o seu código no google code é que todo o seu código é aberto, ou seja outros usuários poderão ver o seu código, mas ninguém poderá fazer modificações sem a sua autorização (A não ser se o seu projeto for milionário =P e necessite de um repositório mais seguro com senha, te recomendo pagar um servidor ou utilizar os exemplos que darei ao final do artigo de servidores privados e gratuitos ).

Bom, logue com sua conta do google e acesse o seguinte link: http://code.google.com/hosting/createProject Coloque as informações sobre o seu projeto como nome, descrição, tipo de licença e etc...

[![](http://javalees.files.wordpress.com/2012/01/captura_de_tela.png)](http://javalees.files.wordpress.com/2012/01/captura_de_tela.png)

Depois de criado o servidor SVN, copie o link de seu repositório (que no meu caso ficou como https://testedeexemplopauloluan.googlecode.com/svn/):

[![](http://javalees.files.wordpress.com/2012/01/captura_de_tela-1.png)](http://javalees.files.wordpress.com/2012/01/captura_de_tela-1.png)

Por convenção utilizamos as pastas Branches, Tags e Trunk. Sendo que Trunk é a versão que está em desenvolvimento constante no dia-a-dia, Branches é um ponto (ou linha) de desenvolvimento do sistema e Tags são “releases” ou versões “liberadas” para o cliente. (este [blog ](//blog.jmfeurprier.com/2010/02/08/svn-trunk-branches-and-tags/”) em inglês explica este conceito). Por padrão o google code já cria estas pastas para nós!

[![](http://javalees.files.wordpress.com/2012/01/captura_de_tela-2.png)](http://javalees.files.wordpress.com/2012/01/captura_de_tela-2.png)

Abra novamente o eclipse mude a perspectiva do eclipse para SVN Repository Exploring...

[![](http://javalees.files.wordpress.com/2012/01/captura_de_tela-java-ee-eclipse-1.png)](http://javalees.files.wordpress.com/2012/01/captura_de_tela-java-ee-eclipse-1.png)

Selecione como na imagem:

[![](http://javalees.files.wordpress.com/2012/01/captura_de_tela-4.png)](http://javalees.files.wordpress.com/2012/01/captura_de_tela-4.png)

Agora clique com o botão direito → new repository location

[![](http://javalees.files.wordpress.com/2012/01/captura_de_tela-svn-repository-exploring-eclipse.png)](http://javalees.files.wordpress.com/2012/01/captura_de_tela-svn-repository-exploring-eclipse.png)

coloque o endereço do meu (ou o repositório que vocês criou) repositório para você fazer o download:

[![](http://javalees.files.wordpress.com/2012/01/captura_de_tela-6.png)](http://javalees.files.wordpress.com/2012/01/captura_de_tela-6.png)

Eis que temos nosso repositório criado no google acessado pelo eclipse :D clique com o botão direito na pasta trunk e clique em “Checkout” para baixar esta pasta para seu computador!

[![](http://javalees.files.wordpress.com/2012/01/captura_de_tela-svn-repository-exploring-eclipse-1.png)](http://javalees.files.wordpress.com/2012/01/captura_de_tela-svn-repository-exploring-eclipse-1.png)

Deixe as configurações do jeito que estão e clique em “finish”

[![](http://javalees.files.wordpress.com/2012/01/captura_de_tela-10.png)](http://javalees.files.wordpress.com/2012/01/captura_de_tela-10.png)

é aqui criaremos o tipo de projeto que queremos! Isso dependerá do que você vai fazer, no nosso projeto vou criar um projeto java simples com um “Hello World” (mas você pode criar o projeto que você quiser ;) ), clique em “next”

[![](http://javalees.files.wordpress.com/2012/01/captura_de_tela-11.png)](http://javalees.files.wordpress.com/2012/01/captura_de_tela-11.png)

nesta tela daremos o nome do nosso projeto, clique em “finish”:

[![](http://javalees.files.wordpress.com/2012/01/captura_de_tela-12.png)](http://javalees.files.wordpress.com/2012/01/captura_de_tela-12.png)

o eclipse vai perguntar se você quer modificar a visão para java, clique em “yes”. Nosso repositório será baixado pelo eclipse!

[![](http://javalees.files.wordpress.com/2012/01/captura_de_tela-13.png)](http://javalees.files.wordpress.com/2012/01/captura_de_tela-13.png)

Nosso projeto foi baixado! Agora vamos criar a classe java com o “hello world“ para isto clique com o botão direito em src --> new Class , Coloque o nome de Hello Word e clique em finish, o resultado será parecido com este:

[![](http://javalees.files.wordpress.com/2012/01/captura_de_tela-15.png)](http://javalees.files.wordpress.com/2012/01/captura_de_tela-15.png)

Criada a classe vamos agora enviá-la para o nosso repositório através do commit! Para isto clique no projeto com o botão direito → Team → commit ,

[![](http://javalees.files.wordpress.com/2012/01/captura_de_tela-java-helloword-src-br-com-javalees-helloworld-java-eclipse.png)](http://javalees.files.wordpress.com/2012/01/captura_de_tela-java-helloword-src-br-com-javalees-helloworld-java-eclipse.png)

Coloque no comentários o motivo do commit que está sendo feito.

[![](http://javalees.files.wordpress.com/2012/01/captura_de_tela-16.png)](http://javalees.files.wordpress.com/2012/01/captura_de_tela-16.png)

Coloque o nome de usuário e senha que pode ser configurado na [sua conta do google](//code.google.com/hosting/settings).

[![](http://javalees.files.wordpress.com/2012/01/captura_de_tela-17.png)](http://javalees.files.wordpress.com/2012/01/captura_de_tela-17.png)

Após o coomit ser efetuado entre em seu projeto (acesse do seu browser), repare que os arquivos foram adicionados com sucesso no repositório criado no google a partir de seu commit dado no eclipse!!

[![](http://javalees.files.wordpress.com/2012/01/captura_de_tela-18.png)](http://javalees.files.wordpress.com/2012/01/captura_de_tela-18.png)

Agora você tem um repositório que pode ser dividido entre os usuários que vocês quiser! Ou seja se for um trabalho da faculdade, basta criar os usuários que poderão realizar commits em seu repositório e que todos os membros do grupo baixem os arquivos do repositório e seguir os procedimentos descritos no tutorial =)

No meu caso, eu decidi criar alguns projetos com meus amigos, pois estávamos perdendo tempo e muitas linhas de código com a troca via e-mail (pois muitas vezes não estamos próximos um do outro (ou sem internet), o que dificulta passar os arquivos), além de que é horrível juntar todas as partes sem ter nenhuma ideia de qual arquivo foi modificado ou não.
Minha necessidade então, foi a de arrumar um servidor SVN gratuito e privado (que tivesse senha para acesso ao repositório), foi então que encontrei dois serviços muito interessantes que preencheram os meus requisitos! Pois a maioria destes serviços gratuitos deixam o seu código open-source (isso varia da necessidade de cada um, se não se importar em deixar o seu código aberto existem muitos outros servidores gratuitos e que oferecem um serviço de bastante qualidade!).
O dois servidores citados abaixo supriram minhas necessidades:

http://beanstalkapp.com/

http://xp-dev.com

Ambos oferecem serviços gratuitos e privados (mas com muitas limitações) de hospedagem de repositório SVN (não encontrei nenhum outro servidor SVN nestas condições, caso você saiba de algum outro deixe nos comentários).

A lista abaixo contém vários servidores SVN gratuitos (mas não privados)

http://www.assembla.com/
http://unfuddle.com/
http://www.berlios.de/
https://opensvn.csie.org/
http://projectlocker.com/
http://sourceforge.net/
http://www.kinghost.com.br/svn
http://www.visualsvn.com/
http://www.siteground.com/subversion-hosting.htm
http://www.bordom.net/view/11977/DevjaVu_-_Free_Trac_SVN_Hosting
http://www.codeplex.com/

Este post te ajudou? Poste nos comentários o que achou! Ficarei feliz em saber que meu domingo valeu a pena ahuashuha (demorei alguns dias pra reunir todas estas informações então aproveite ;D) abraços!
