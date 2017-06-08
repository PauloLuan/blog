---
layout: post
title: "Aumente o desempenho do Mac Removendo efeitos de animação"
date: 2013-11-07 17:17
comments: true
categories: 
---

Utilize os comandos abaixo para remover os efeitos do Mac e aumentar o seu desempenho.

<!-- more -->

``` bash
# opening and closing windows and popovers
defaults write -g NSAutomaticWindowAnimationsEnabled -bool false
```


``` bash
# smooth scrolling
defaults write -g NSScrollAnimationEnabled -bool false
```


``` bash
# showing and hiding sheets, resizing preference windows, zooming windows
# float 0 doesn't work
defaults write -g NSWindowResizeTime -float 0.001
```


``` bash
# opening and closing Quick Look windows
defaults write -g QLPanelAnimationDuration -float 0
```


``` bash
# rubberband scrolling (doesn't affect web views)
defaults write -g NSScrollViewRubberbanding -bool false
```


``` bash
# resizing windows before and after showing the version browser
# also disabled by NSWindowResizeTime -float 0.001
defaults write -g NSDocumentRevisionsWindowTransformAnimation -bool false
```

``` bash
# showing a toolbar or menu bar in full screen
defaults write -g NSToolbarFullScreenAnimationDuration -float 0
```

``` bash
# scrolling column views
defaults write -g NSBrowserColumnAnimationSpeedMultiplier -float 0
```

``` bash
# showing the Dock
defaults write com.apple.dock autohide-time-modifier -float 0
defaults write com.apple.dock autohide-delay -float 0
```

``` bash
# showing and hiding Mission Control, command+numbers
defaults write com.apple.dock expose-animation-duration -float 0
```

``` bash
# showing and hiding Launchpad
defaults write com.apple.dock springboard-show-duration -float 0
defaults write com.apple.dock springboard-hide-duration -float 0
```

``` bash
# changing pages in Launchpad
defaults write com.apple.dock springboard-page-duration -float 0
```

``` bash
# at least AnimateInfoPanes
defaults write com.apple.finder DisableAllAnimations -bool true
```

``` bash
# sending messages and opening windows for replies
defaults write com.apple.Mail DisableSendAnimations -bool true
defaults write com.apple.Mail DisableReplyAnimations -bool true
```

``` bash
killall Dock
```

Sources:

http://www.chriswrites.com/2012/01/turn-off-animations-eye-candy-effects-in-mac-os-x-lion/

http://unsanity.com/haxies/shadowkiller

http://apple.stackexchange.com/questions/14001/how-to-turn-off-all-the-animation-effect-on-mac-os
