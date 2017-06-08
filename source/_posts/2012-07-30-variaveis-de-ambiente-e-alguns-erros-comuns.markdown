---
author: pauloluan
comments: true
date: 2012-07-30 19:35:11
layout: post
slug: variaveis-de-ambiente-e-alguns-erros-comuns
title: Variáveis de ambiente e alguns erros comuns.
wordpress_id: 660
categories:
- Metodologias
tags:
- ambiente
- android
- classpath
- home
- java
- javahome
- path
- titanium
- variáveis
- windows
---

Estava eu programando no WINDOWS sim, WINDOWS (SDK de uma ferramenta que só funciona no Windows) :(( rs quando eu me deparei com o seguinte erro com a plataforma Titanium:

<!-- more -->

``` bash

[INFO] logfile = C:UsersPauloLuanDropboxSource CodesOnibusSJCworkTitaniumOnibusSJCbuild.log
[INFO] Launching Android emulator...one moment
[ERROR] 'xcopy' não é reconhecido como um comando interno
[ERROR] ou externo, um programa operável ou um arquivo em lotes.
[ERROR] Exception occured while building Android project:
[ERROR] Traceback (most recent call last):
[ERROR] File "C:UsersPauloLuanAppDataRoamingTitaniummobilesdkwin322.1.0.GAandroidbuilder.py", line 2199, in
[ERROR] s.run_emulator(avd_id, avd_skin, avd_name, avd_abi, add_args)
[ERROR] File "C:UsersPauloLuanAppDataRoamingTitaniummobilesdkwin322.1.0.GAandroidbuilder.py", line 476, in run_emulator
[ERROR] avd_name = self.create_avd(avd_id, avd_skin, avd_abi)
[ERROR] File "C:UsersPauloLuanAppDataRoamingTitaniummobilesdkwin322.1.0.GAandroidbuilder.py", line 399, in create_avd
[ERROR] available_avds = avd.get_avds(self.sdk)
[ERROR] File "C:UsersPauloLuanAppDataRoamingTitaniummobilesdkwin322.1.0.GAandroidavd.py", line 23, in get_avds
[ERROR] for line in run.run([sdk.get_android(),'list','target'],debug=False).split("n"):
[ERROR] AttributeError: 'NoneType' object has no attribute 'split'
```



// 
// 


No começo não sabia o que fazer, mas ao analisar a terceira linha vi que a mensagem dizia: "'xcopy' não é reconhecido como um comando interno" estranhei porque xcopy é um comando do windows no cmd para copia de arquivos, pois bem, o problema que ocasionou este erro na minha IDE é que as variáveis de ambiente do windows estavam desconfiguradas, eu acho que de tanto mexer pra configurar o meu Java (é que estava tendo alguns problemas), no entanto, se você quiser saber mais sobre as variáveis de ambiente leia [este](http://pt.wikipedia.org/wiki/Vari%C3%A1vel_de_ambiente) e [este](http://technet.microsoft.com/pt-br/library/cc668471.aspx) artigo.

Por exemplo, quando retiramos a propriedade "C:WindowsSystem32" das variáveis de Path teremos alguns erros como os seguintes:

``` bash
'xcopy' não é reconhecido como um comando interno ou externo, um programa operável ou um arquivo em lotes.
'ipconfig' não é reconhecido como um comando interno ou externo, um programa operável ou um arquivo em lotes.
```

semelhante a imagem:

[caption id="attachment_671" align="aligncenter" width="676"][![Erro: cmd não reconhece comandos.](http://javalees.files.wordpress.com/2012/07/erros-cmd-nc3a3o-reconhece.png)](http://javalees.files.wordpress.com/2012/07/erros-cmd-nc3a3o-reconhece.png) Erro: cmd não reconhece comandos.[/caption]

pois todos os programas que estavam mapeados agora não estão mais, as variáveis de ambiente são importantes e é só você colocar o diretório onde estão os executáveis que o sistema mapeará e deixará disponível para uso no terminal.

Então para configurar basta pressionar o "logo do windows + pause break" ou ir no painel de controle --> Sistema --> variáveis de ambiente. O importante é chegar nesta tela:

[caption id="attachment_672" align="aligncenter" width="421"][![Propriedades do Sistema](http://javalees.files.wordpress.com/2012/07/propriedades-do-sistema.png)](http://javalees.files.wordpress.com/2012/07/propriedades-do-sistema.png) Propriedades do Sistema[/caption]

Depois clique em variáveis de ambiente:

[caption id="attachment_673" align="aligncenter" width="393"][![Variáveis de ambiente](http://javalees.files.wordpress.com/2012/07/varic3a1veis-de-ambiente.png)](http://javalees.files.wordpress.com/2012/07/varic3a1veis-de-ambiente.png) Variáveis de ambiente[/caption]

e depois é só clicar em "editar" sobre a variável de ambiente PATH e colar o local a ser mapeado por exemplo, se você quiser que o Java seja mapeado coloque o diretório da instalação (geralmente é o "C:Program Files (x86)Javajdk1.7.0_05bin;" ou algo parecido ;) ) e lembre-se de separar as pastas com ";" ,logo, para resolver aquele problema da minha IDE era só colocar o caminho "C:WindowsSystem32" na variável PATH como na imagem:

com as variáveis de ambiente configuradas olha que bonito que ficou meu CMD executando o comando xcopy e ipconfig:

[caption id="attachment_670" align="aligncenter" width="677"][![cmd feliz](http://javalees.files.wordpress.com/2012/07/cmd-feliz.png)](http://javalees.files.wordpress.com/2012/07/cmd-feliz.png) cmd feliz[/caption]

Att, Paulo Luan.
