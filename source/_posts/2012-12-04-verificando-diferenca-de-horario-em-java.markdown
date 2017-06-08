---
author: pauloluan
comments: true
date: 2012-12-04 10:46:50
layout: post
slug: verificando-diferenca-de-horario-em-java
title: Verificando diferença de horário em Java
wordpress_id: 799
categories:
- Java
tags:
- date
- diferença
- horas
- hour
- java
---

``` java 

public void verificaDiferenca() {
		String data = "08/12/2003";
		String hora_saida = "19:00:00";

		SimpleDateFormat sdf = new SimpleDateFormat("dd/MM/yyyy HH:mm:ss");
		SimpleDateFormat df = new SimpleDateFormat("HH:mm:ss");
		Date hora = new Date();
		Date horaS = new Date();
		Date diferenca = new Date();

		try {
			horaS = sdf.parse(data + " " + hora_saida);
		} catch (ParseException p) {
			System.out.println(p.getMessage());
		}

		diferenca.setTime(hora.getTime() - horaS.getTime());

		System.out.println("hora saida " + sdf.format(horaS));
		System.out.println("hora retorno " + sdf.format(hora));
		System.out.println("diferenca " + df.format(diferenca));

		long difMilli = hora.getTime() - horaS.getTime();
		int timeInSeconds = (int) difMilli / 1000;
		int hours, minutes, seconds;
		hours = timeInSeconds / 3600;
		timeInSeconds = timeInSeconds - (hours * 3600);
		minutes = timeInSeconds / 60;
		timeInSeconds = timeInSeconds - (minutes * 60);
		seconds = timeInSeconds;
		System.out.println(hours + " hour(s) " + minutes + " minute(s) "+ seconds + " second(s)");
	}

```

Fonte: http://javafree.uol.com.br/topic-2263-diferencas-entre-data-e-horarios.html
