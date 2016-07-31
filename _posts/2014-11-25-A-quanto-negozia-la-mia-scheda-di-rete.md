---
layout: post
title: "Verifica a quanto negozia la scheda di rete di un client"
modified:
categories:
excerpt:
tags: [Network]
image:
  feature:
date: 2014-11-25
comments: true
---

Tutte le volte mi perdo il comando. Lo metto sul blog così lo ritrovo la prossima volta che non ho accesso agli switch. Per verificare a quanto negozia la scheda di rete di un client **Windows 7/8** è sufficiente lanciare questo comando:
{% highlight bash %}
wmic nic NetEnabled=true where "macaddress <> null" get NetConnectionID,macaddress,Speed
{% endhighlight %}

L'output è di questo tipo:<br>
![speed]({{ site.url }}/images/img_post/Network/wmnic.png)

Poi si può modificare la query con altri parametri, dipende cosa si vuole ottenere:
{% highlight bash %}
wmic nic NetEnabled=true where "macaddress <> null" list full
{% endhighlight %}

Lo stesso comando non funziona su macchine ***Windows Xp***, per cui va lanciato il seguente comando:
{% highlight bat %}
wmic /namespace:\\root\wmi path MSNdis_LinkSpeed
{% endhighlight %}

In questo caso l'output sarà simile al seguente:
{% highlight text %}
C:\>wmic /namespace:\\root\wmi path MSNdis_LinkSpeed
Active  InstanceName                                                       NdisLinkSpeed
TRUE    WAN Miniport (IP)                                                  288
TRUE    WAN Miniport (IP) - Packet Scheduler Miniport                      288
TRUE    VMware Accelerated AMD PCNet Adapter                               10000000
TRUE    AMD PCNET Family PCI Ethernet Adapter - Packet Scheduler Miniport  10000000
TRUE    RAS Async Adapter                                                  288
{% endhighlight %}