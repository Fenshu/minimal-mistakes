---
layout: post
title: "Cryptomator. File al sicuro, con chiave locale"
published: false
modified:
categories:	Mac
excerpt:
tags: []
image:
  feature:
date: 2015-11-18
comments: true
---

Chi più chi meno abbiamo da gestire documenti elettronici di una certa riservatezza. C'è chi salva le buste paga, chi i contratti di collaborazione, chi i documenti bancari e via discorrendo. Il problema della sicurezza, in questi specifici casi, non può essere affrontata senza un minimo di considerazioni.<br>

La parola sicurezza in informatica è un termine da trattare con le pinze. Senza entrare nel dettaglio o in discorsi hacker-filosofici dobbiamo prima capire l'entità dei dati che consideriamo sensibili, e da chi vogliamo difenderci. La storia è piena di dichiarazioni/azioni che dimostrano l'esistenza di agenzie che utilizzano tecniche di intrusione che aggirano i sistemi di sicurezza più raffinati, senza contare che la maggior parte dei reati informatici partono dalla cosiddetta "ingegneria sociale", cioè acquisendo informazioni riservate direttamente dalle persone coinvolte. Se l'aspettativa è mettere il nostro Password_banca.txt al sicuro da chiunque... bè, l'aspettativa a mio giudizio è vana. Se l'esigenza è invece quella di difenderci da cyber-furfantelli allora il web ci mette a disposizione una miriade di tool capaci di mettere in ragionevole sicurezza i nostri dati.<br>
Nel tempo ho testato alcuni software, e mi sono sempre trovato bene con BoxCryopor Classic (non web).

<div style="text-align:center" markdown="1">
![0x80070043]({{ site.url }}/images/img_post/Windows/Error_0x80070043.png)
</div>

Non mi è chiaro *il perchè* capiti questo problema, ma quando capita **non è più possibile fare il *browse* delle share di rete usando esplora risorse.**<br>

## Workaround:
1. Lanciare `regedit` dal prompt dei comandi, con i diritti amministrativi
2. Posizionarsi in <br> `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Contro l\NetworkProvider\HwOrder\`
3. Editare la *dword* `ProviderOrder`
4. Sostituire il contenuto con il seguente valore:<br>
`WDNP32,SnacNp,RDPNP,LanmanWorkstation,webclient`


Non è necessario riavviare, provate nuovamente ad effettuare il *mount* di una risorsa di rete condivisa in modo da verificare subito se il workaround è stato risolutivo.