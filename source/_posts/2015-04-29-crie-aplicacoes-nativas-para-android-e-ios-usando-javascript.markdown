---
layout: post
title: "Crie aplicações nativas para Android e IOS usando Javascript"
date: 2015-04-29 13:29
comments: true
categories: [titanium, alloy, mobile, web, js, javascript]
---

{% img /images/titanium.png %}

Não deixem que te enganem, usar Phonegap com frameworks web faz com que sua aplicação tenha um desempenho ridiculamente ruim, é até bonito pra palestrar nos eventos e te ludibriar, mas se você quer uma aplicação que tenha desempenho e que seja multiplataforma use um framework que faça aplicações nativas, como o [Titanium](http://www.appcelerator.com/product/) ou [ReactNative](https://facebook.github.io/react-native/). Neste tutorial vamos ver como funciona o Titanium e te dar o caminho das pedras para virar um mestre!.

<!-- more -->

Sou pragmático, odeio ler artigos grandes que falam um monte de bláblá pra pouco código. Então vamos direto ao ponto, para você aprender a programar na parada você vai ter que ler códigos prontos e que funcione, então se você quer ver código antes de ler o artigo ai vai uma dica de ouro, clone os repositórios abaixo, eles contém códigos funcionais de exemplos com Titanium, as instruções sobre como rodar estão muito bem descritas [aqui](https://github.com/appcelerator/alloy#getting-started) se vira aí manolo ;) :

https://github.com/appcelerator/alloy/tree/master/test/apps
https://github.com/appcelerator/KitchenSink

## Titanium 

Titanium Mobile é uma plataforma híbrida nativa que permite que a aplicação seja compilada para as plataformas Android e IOS, além de um esforço inicial para BlackBerry. Utiliza a linguagem de programação javascript, mas, apesar desta premissa os aplicativos não são executados por meio de um navegador, em vez disto a arquitetura da linguagem de programação é utilizada para interpretar os códigos desenvolvidos.

O funcionamento básico de uma aplicação Titanium é uma base de código javascript que é interpretada em tempo de execução por um interpretador que é embutido na aplicação no momento de sua compilação. Já o código-fonte visual é compilado para a respectiva plataforma, mantendo o comportamento e aparência da plataforma de destino.

Em uma aplicação Titanium grande parte do código-fonte é utilizado por ambas as plataformas, mas como cada sistema operacional possui alguns comportamentos e funcionalidades específicas, estes códigos podem ser tratados de maneira separada, de forma a permitir a exploração de determinada funcionalidade sem comprometer o restante da aplicação.

O Titanium é open-source e o seu código-fonte está disponível em https://github.com/appcelerator, além da ferramenta em si, diversos códigos de aplicações de templates podem ser utilizadas como forma de iniciação ao aprendizado (como citado no começo do artigo).

Um fator que diferencia o Titanium das demais plataformas é a facilidade de customização dos componentes visuais, que é refletida na qualidade final da aplicação desenvolvida.  O portfólio  [Built with Titanium](http://www.builtwithtitanium.com/) (construído com Titanium) permite analisar uma quantidade razoável de aplicativos que foram desenvolvidos utilizando a plataforma, a melhor forma de avaliar se uma plataforma ou framework é bom, é vendo as aplicações que foram feitas e colocadas em produção.

Uma loja de componentes, chamada Marketplace, permite a comercialização de componentes para a plataforma, seja ela desktop (componentes para a IDE) ou para mobile, como componentes visuais, bibliotecas, entre outros.

No site da empresa [Appcelerator](http://www.appcelerator.com/developers), uma vasta documentação se faz presente, contendo a análise detalhada de todos os componentes seguidos de seu exemplo prático. Além da documentação comum, existe um [treinamento gratuito](https://university.appcelerator.com/) para a certificação de desenvolvedor Titanium, que mostra a fundo a arquitetura da aplicação e seus derivados.

A empresa Appcelerator é parceira da international data corporation (IDC) e anualmente faz pesquisas sobre o mercado de desenvolvimento móvel, mostrando através de indicadores, os dados relevantes sobre os rumos que o mercado móvel está sendo direcionado. Todas as pesquisas são abertas e encontram-se disponível no site http://www.appcelerator.com/thinkmobile/surveys.

## Prática

Você vai ter que ter o NodeJS instalado na sua máquina, se estiver no Linux eu recomendo o [NVM](https://github.com/creationix/nvm) e se estiver no windows use o [Chocolatey](http://pauloluan.github.io/blog/blog/2015/04/28/apt-get-no-windows/).

Para instalar leia o README dos projetos [titanium](https://github.com/appcelerator/titanium/blob/master/README.md) e [Alloy](https://github.com/appcelerator/alloy/blob/master/README.md)

Como sou bonzinho, vou dar uns toques abaixo:

## Configurando o SKD do Android

Instale o JAVA7 no seu computador (pra facilitar sua vida use o [Chocolatey](http://pauloluan.github.io/blog/blog/2015/04/28/apt-get-no-windows/) se estive no windows, mas é claro que você está no Linux, isso é óbvio).

[Eu traduzi daqui essa parte](https://spring.io/guides/gs/android/)

1 No [site do android](http://developer.android.com/sdk/index.html) Faça o download do arquivo para o seu sistema operacional.

2 Descompacte o arquivo em um local de sua escolha. Por exemplo, no Linux ou Mac, você pode colocá-lo na raiz do seu diretório de usuário. Consulte o site [Android Developers](http://developer.android.com/sdk/installing/index.html) para obter detalhes de instalação adicionais.

3 Configure a variável de ambiente ANDROID_HOME com base onde você descompactou a parada. Para fazer isso siga os passos:

Mac OS X
{% codeblock lang:bash %}
  export ANDROID_HOME=/<installation location>/android-sdk-macosx
  export PATH=${PATH}:$ANDROID_HOME/tools:$ANDROID_HOME/platform-tools
{% endcodeblock %}

Linux
{% codeblock lang:bash %}
  export ANDROID_HOME=/<installation location>/android-sdk-linux
  export PATH=${PATH}:$ANDROID_HOME/tools:$ANDROID_HOME/platform-tools
{% endcodeblock %}

Windows
{% codeblock lang:bash %}
  set ANDROID_HOME=C:\<installation location>\android-sdk-windows
  set PATH=%PATH%;%ANDROID_HOME%\tools;%ANDROID_HOME%\platform-tools
{% endcodeblock %}

O download do Android SDK não inclui os SDK's das plataformas específicas. Para executar o código neste tutorial, você precisa baixar e instalar a plataforma SDK mais recente. Para fazer isso siga comigo:

1. Abra um terminal e digite: `android` (se não funcíonar é sinal de que você não configurou direito a variável de ambiente).
2. Selecione `Tools`.
3. Selecione a última versão do SDK disponível.
4. A partir da pasta `Extras`, selecione o checkbox `Android Support Library`.
5. Clique no botão `Install packages…` e a instalação vai começar (e vai demorar um pouco hein...).

## Configurando Titanium e Alloy:

Instale o Titanium e Alloy `npm install -g titanium alloy` 

Crie uma conta na appcelerator e logue depois no terminal `ti login <usuario> <senha>`

Baixe o SDK do titanium `titanium sdk install` ele vai baixar a ultima versão.

Faça o setup do titanium: `titanium setup` 

Tudo pronto agora é só pegar aquele [README](https://github.com/appcelerator/alloy#getting-started) que eu falei pra você ler do Alloy e executar os exemplos com [Alloy](https://github.com/appcelerator/alloy/tree/master/test/apps) e [Titanium puro](https://github.com/appcelerator/KitchenSink).

