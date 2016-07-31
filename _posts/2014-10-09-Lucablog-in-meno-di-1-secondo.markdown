---
layout: post
title: "Lucablog.it in meno di 1 secondo"
modified:
categories:
excerpt:
tags: [web,Jekyll,DNS,Cloud,CloudFlare]
image:
  feature:
date: 2014-10-09
comments: true
---

Mi capita, raramente ma capita, di fissarmi su una specifica funzionalità del tool di turno. Adesso mi è capitato con i tempi di caricamento del mio blog. Sarà perchè sono rimasto abbastanza scottato dalle prestazini pachidermiche di Wordpress, sarà perchè adesso ho affidato la delega della mia zona DNS a CloudFlare, sarà che ho eliminato tutto quello che reputo superfluo... fattostà che adesso [Lucablog.it](http://lucablog.it) risulta consultabile in [poco più di mezzo secondo](http://www.webpagetest.org/result/141009_9Y_VJZ/1/details/) :)<br>

![Caricamento di Lucablog con Jakyll]({{ site.url }}/images/img_post/webspeed_Lucablog_Jekyll_1.jpg)

Facendo un confronto con Wordpress, con plugin disabilitati, i tempi erano ben altri:<br>
![Caricamento di Lucablog con Wordpress]({{ site.url }}/images/img_post/webspeed_Lucablog_WP.png)

Volendo ben vedere potrei ottimizzare ulterioremente i tempi di caricamento, evitando di caricare il font "PT Serif" che risulta essere un pò pesantuccio. Ma va bene così.