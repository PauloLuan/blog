---
author: pauloluan
comments: true
date: 2012-01-18 20:23:07
layout: post
slug: hello-world-em-javafx-2-0
title: Hello World em JavaFX 2.0
wordpress_id: 199
categories:
- JavaFX
tags:
- '2.0'
- aplicação
- external jars
- hello
- java
- java project
- JavaFX
- language java
- primeira
- world
---

Leia:
[O que é JavaFX 2.0?](http://javalees.wordpress.com/2012/01/19/o-que-e-o-javafx-2-0/)
[Como Instalar JavaFX 2.0](http://javalees.wordpress.com/2012/01/18/como-instalar-javafx-2-0/)




Talvez por ser um produto da Oracle, a [IDE NetBeans](//netbeans.org/) já é bem preparada para criar aplicações para JavaFX, no entanto, devido a esta facilidade vou fazer este tutorial demonstrando como criar aplicações JavaFX no Eclipse, que também é uma ótima IDE ;) então mãos à obra.




<!-- more -->




Esta aplicação pode ser criada em qualquer IDE do Eclipse versão Java, para começarmos, crie um novo Java Project, clicando com o botão direito --> New --> Java Project,  nomeie-o da maneira que quiser, e clique em Next:




[![](http://javafxbr.com/blog/wp-content/uploads/2012/01/1.jpg?w=1024)](http://javafxbr.com/blog/wp-content/uploads/2012/01/1.jpg)




[![](http://javafxbr.com/blog/wp-content/uploads/2012/01/2.jpg?w=1024)](http://javafxbr.com/blog/wp-content/uploads/2012/01/2.jpg)




Clique na Aba Libraries, É aqui que ocorre a mágica hehe nós teremos que incluir o JAR externo que contém o conjunto de instruções do JavaFX, para isto clique em Add External Jars




[![](http://javafxbr.com/blog/wp-content/uploads/2012/01/3.jpg?w=1024)](http://javafxbr.com/blog/wp-content/uploads/2012/01/3.jpg)




Por padrão, o diretório de instalação é o X:Program FilesOracleJavaFX 2.0 SDKrtlibjfxrt.jar é este o caminho que teremos que indicar conforme a figura abaixo:




[![](http://javafxbr.com/blog/wp-content/uploads/2012/01/4.jpg?w=1024)](http://javafxbr.com/blog/wp-content/uploads/2012/01/4.jpg)




Depois disto, crie uma classe Java com qualquer nome, pode ser como no exemplo “TesteFX” e coloque o seguinte código:



``` java package javalees.wordpress.com;

import javafx.application.Application;
import javafx.scene.Group;
import javafx.scene.Scene;
import javafx.scene.text.Text;
import javafx.stage.Stage;

/**
 * @author PauloLuan
 */
public class TesteFX extends Application {
	/*
	 * repare que nossa classe herda da Classe Application, que é a classe que
	 * fornece todo o ciclo de vida para as aplicações em JavaFX
	 */

	/* Este método é obrigatório pois é herdado da classe Application */

	@Override
	public void start(Stage stage) throws Exception {
		/*
		 * O Stage do parâmetro é o contâiner de nível superior como se fosse o
		 * "palco" principal da aplicação, e a "cena" (Scene) é a superfície de
		 * desenho para o conteúdo do aplicativo.
		 */

		/*
		 * Uma aplicação JavaFX é composta por uma árvore hierárquica de nós,
		 * quando criamos uma cena temos que aderí-la à um grupo Pai que vai ser
		 * o seu nó superior. Isto fica explicito abaixo quando criamos a cena e
		 * passamos como parâmetro uma nova instância de um Grupo. Não entendeu?
		 * (nem eu! kkk brincadeira) o seguinte link demonstra uma aplicação de
		 * círculos coloridos:
		 *
		 * http://docs.oracle.com/javafx/2.0/get_started/jfxpub-get_started.htm
		 *
		 * Nesta aplicação fica mais fácil compreender a estrutura hieráquica de
		 * uma aplicação JavaFX.
		 */
		Scene scene = new Scene(new Group(new Text(250, 30,
				"JavaLees says: Hello World, JavaFX!")));

		stage.setTitle("Hello World | JavaLees"); // modificamos o título do Janela
		stage.setScene(scene); // enviamos a "cena"(Scene) desenhada para o contâiner superior (Stage)
		stage.show(); // método que faz com que a aplicação seja exibida
	}

	public static void main(String[] args) {
		launch(args); // único método chamado na classe Main que dispara nossa aplicação.
	}
}```


Eis que temos nossa primeira aplicação em JavaFX 2.0! :D





[![primeira aplicação em javaFX!](http://javafxbr.com/blog/wp-content/uploads/2012/01/6.jpg)](http://javafxbr.com/blog/wp-content/uploads/2012/01/6.jpg)
    primeira aplicação em javaFX!




[Aqui na Documentação](//docs.oracle.com/javafx/index.html) você encontra detalhes importantes sobre toda a estrutura e os componentes de uma aplicação do JavaFX.




[twitter-follow screen_name='javalees' show_count='no' text_color='00ccff']
