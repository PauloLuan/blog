---
author: pauloluan
comments: true
date: 2012-11-01 12:56:01
layout: post
slug: how-to-install-homebrew-on-macos-over-http-proxy
title: How to Install HomeBrew on MacOS over HTTP Proxy
wordpress_id: 788
categories:
- Metodologias
tags:
- como
- homebrew
- instalar
- mac
- macports
- os
---

``` bash
	export http_proxy=http://192.168.1.1:3128
	export ALL_PROXY=$http_proxy
	ruby -e "$(curl -fsSkL raw.github.com/mxcl/homebrew/go)"
```
<!-- more -->
Sources:
http://squarism.com/2010/12/14/homebrew-behind-a-proxy/
https://github.com/mxcl/homebrew/wiki/Tips-N'-Tricks
http://stackoverflow.com/questions/9904850/how-to-install-homebrew-on-mac-osx-snow-leopard
