---
layout: post
title: "NAS Qnap ed il processo utilRequest.cgi"
modified:
categories: 
excerpt:
tags: []
image:
  feature:
date: 2014-09-18T10:29:43+02:00
---

Se avete un problema simile al mio, ovvero se il processo utilRequest.cgi occupa quasi il 100% del processore, potete sistemare cancellando il file share_link.db. Accediamo al Nas con via ssh, e lanciamo i seguenti comandi:

{% highlight bash %}	
cd /mnt/HDA_ROOT/.config
rm share_link.db
{% endhighlight %}

Dopo il riavvio non ho più avuto problemi.