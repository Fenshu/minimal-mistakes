---
layout: post
title: "Certificato SSL per GitHub gratis, con CloudFlare"
published: true
modified:
categories:	Web
excerpt:
tags: []
image:
  feature:
date: 2015-10-12
comments: true
---

<a href="https://www.cloudflare.com" target="_blank">CloudFlare</a> continua a darmi grandi soffisfazioni. Lasciamo perdere la mera e noiosa gestione degli **RR Record** sui DNS, parliamo della bella e mai-scontata feature che permette, anche per il proprio blog/sito hostato su GitHub, di usare un **certificato SSL pubblicamente riconosciuto**.<br>

<div style="text-align:center" markdown="1">
![SSL]({{ site.url }}/images/img_post/Web/SSL_CloudFlare/Cert_Lucablog.png)
</div>

Via, pannello di controllo di CloudFlare, clicchiamo il bottone `Crypto` nella top bar.<br>
Alla voce **SSL (with SPDY)** va selezionato **Flexible**, se non fosse già così.<br>

<div style="text-align:center" markdown="1">
![SSL]({{ site.url }}/images/img_post/Web/SSL_CloudFlare/SSL_Flexible.png)
</div>

**ATTENZIONE:** una volta modificato il profilo SSL sarà necessario attendere fino a 48 ore.<br>
Alla voce `Page Rules` possiamo creare le regole di *redirect*, dall'http all'https, mettendo semplicemente ad **ON** la voce **Always use https**. Nel mio caso:

<div style="text-align:center" markdown="1">
![SSL]({{ site.url }}/images/img_post/Web/SSL_CloudFlare/Rules.png)
</div>

Questo è quanto.