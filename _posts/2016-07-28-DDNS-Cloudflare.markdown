---
layout: post
title: "CloudFlare - DNS dinamico"
published: true
categories: 
excerpt:
tags: [web,Jekyll]
image:
  feature:
date: 2016-07-28
comments: true
---

Chi possiede un abbonamento ADSL "per privati", e ha bisogno di poter raggiungere il proprio server casalingo, deve fare necessariamente i conti con l'ip che viene generato dinamicamente dal provider. Fino poco tempo fa usavo il servizio gratuito di ddns, offerto da *no-ip*. Il problema è che ogni tot giorni si è costretti a collegarsi sul *noip.com*, confermare che non si è un robot<br>
Uhm... no! :)<br>
Vi ho già parlato di **CloudFlare**, e torno a parlarne perchè mette a disposizione dei suoi clienti (anche con il profilo *free*, come il mio) uno script che sostituisce il servizio ddns/noip. Questo script si chiama **ddclient**, ed è disponibile a [questo indirizzo](http://sourceforge.net/projects/ddclient/).
E' scritto in Perl, dovete quindi accertarvi che la vostra GNUbox abbia a bordo il relativo interprete. Se non l'avesse dovete installarlo:

{% highlight bash %}
apt-get install libio-socket-ip-perl libio-socket-ssl-perl
{% endhighlight %}

Adesso scaricate il client dove volete, estraete il contenuto e procedete con l'installazione ed esecuzione:
{% highlight bash %}
cp ddclient /usr/sbin/
mkdir /etc/ddclient
mkdir /var/cache/ddclient
cp sample-etc_ddclient.conf /etc/ddclient/ddclient.conf
{% endhighlight %}

Personlamente lancio lo script con il mio utente, quindi assicuratevi di avere i permessi giusti su file e cartelle. Adesso va editato il file di configurazione:

{% highlight bash %}
vim /etc/ddclient/ddclient.conf
{% endhighlight %}

Ecco la mia configurazione:

{% highlight text %}
use=web, web=dyndns
protocol=cloudflare,                           \
server=www.cloudflare.com,                     \
login=lavostra@email.com,                          \
password=la_vostra_api_key_glogab              \
zone=vostrodominio.it, \
vostroserver.vostrodominio.it

daemon=300                              # check every 300 seconds
syslog=yes                              # log update msgs to syslog
mail=root                               # mail all msgs to root
mail-failure=root                       # mail failed update msgs to root
pid=/var/run/ddclient.pid               # record PID in file.
ssl=yes                                 # use ssl-support.  Works 
{% endhighlight %}

La conf è finita, avviate il servizio (e/o scriptatelo all'avvio del server... vedete voi):

{% highlight bash %}
ddclient -daemon=0 -debug -verbose -noquiet
{% endhighlight %}

Di seguito le ultime righe del mio log:
{% highlight text %}
RECEIVE:  <html><head><title>Current IP Check</title></head><body>Current IP Address: 151.xx.15x.xx</body></html>
DEBUG:    get_ip: using web, http://checkip.dyndns.org/ reports 151.xx.15x.xx
SUCCESS:  miosito.lucablog.it: skipped: IP address was already set to 151.xx.15x.xx.
{% endhighlight %}

Fine.