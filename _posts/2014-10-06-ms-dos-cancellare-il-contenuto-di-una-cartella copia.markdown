---
layout: post
title: "[MS-DOS] Cancellare il contenuto di una cartella"
modified:
categories: 
excerpt:
tags: []
image:
  feature:
date: 2014-09-18T10:37:44+02:00
comments: true
---

Può sembrare una stupidata, ma con il prompt di DOS per eseguire una semplice operazione di cancellazione ricorsiva che comprenda file, cartelle e sottocartelle, è necessario un piccolo script. Lo posto sul blog, magari viene utile a qualcuno:

{% highlight bat %}
@echo off
 
REM #### Cartella target ####
SET Da_Cancellare=C:\_Temp
REM #########################
 
DEL /F /Q /S %Da_Cancellare%\*
for /D %%i in (%Da_Cancellare%\*) do RD /S /Q "%%i"
exit;
{% endhighlight %}

Qualcuno potrebbe dirmi di cancellare e ricreare la cartella `C:\_Temp`,  ma potremmo non avere i permessi per cancellare la cartella padre.