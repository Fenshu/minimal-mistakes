---
layout: post
title: "Funzione 'Stampa' in Sublime Text (2 e 3)"
published: True
modified:
categories:	Windows
excerpt:
tags: []
image:
  feature:
date: 2015-08-19
comments: true
---

Ci sono molti editor di testo gratuiti e validi, uno tra tutti è *Notepad++*, ma uso con soddisfazione un editor shareware... **Sublime Text**.<br>

<div style="text-align:center" markdown="1">
![Sublmie Test]({{ site.url }}/images/img_post/SublimeText_exemple.png)
</div>

Lo uso perchè è estremamente versatile, edita nativamente i markdown file ed è stato compilato sia per windows che per Mac (ed è il mio caso). Incredibile ma vero, nonostante il programma sia molto potente e personalizzabile fin nei mimini dettagli **manca la funzione di stampa**. Non chiedetemi il motivo, ma sembra che ci siano razionali tecnico-filosofici che spieghino questa mancanza. Bando alle ciance, c'è un modo per ovviare a questa assurda mancanza, sfruttanto un package gratuito che esporta il testo in *html* verso il browser predefinito, pronto per la stampa.<br>
Come si fa?<br>
Attivare la console dal menù `View > Show Console`, **se avete la versione 3 dell'editor** incollare il seguente codice:<br>

{% highlight text %}
import urllib.request,os,hashlib; h = 'eb2297e1a458f27d836c04bb0cbaf282' + 'd0e7a3098092775ccb37ca9d6b2e4b7d'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
{% endhighlight %}

Diversamente, se avete la versione 2 il codice è il seguente:<br>

{% highlight text %}
import urllib2,os,hashlib; h = 'eb2297e1a458f27d836c04bb0cbaf282' + 'd0e7a3098092775ccb37ca9d6b2e4b7d'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); os.makedirs( ipp ) if not os.path.exists(ipp) else None; urllib2.install_opener( urllib2.build_opener( urllib2.ProxyHandler()) ); by = urllib2.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); open( os.path.join( ipp, pf), 'wb' ).write(by) if dh == h else None; print('Error validating download (got %s instead of %s), please try manual install' % (dh, h) if dh != h else 'Please restart Sublime Text to finish installation')
{% endhighlight %}

Battete **invio**. Il **Packege Manager** è installato, continuamo con il pacchetto che ci interessa. Sempre con l'editor aperto digitate `Cmd+Shift+P` cliccate su `Package Control: Install Package`. Dall'elenco che compare selezionate `Print to HTML`, partirà automaticamente l'installer del pacchetto. È tutto.<br>
Per poter inviare il testo in stampa basta premere i tasti `Ctrl+Shift+P`, oppure dal menù `File > Print as HTML to Browser`