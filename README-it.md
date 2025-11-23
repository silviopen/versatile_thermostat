[![GitHub Release][releases-shield]][releases]


# Versatile thermostat

Questo file README è disponibile in lingue : [English](README.md) | [Čeština](README-cs.md) | [Deutsch](README-de.md) | [Français](README-fr.md) | [Italiano](README-it.md) | [Deutsch](README-de.md) | [Polski](README-pl.md)
<div> <br> </div>
<p align="center">
<img src="https://github.com/jmcollin78/versatile_thermostat/blob/main/images/icon.png" />
</p>

> ![Suggerimento](images/tips.png) Suggerimento

Questa integrazione del termostato mira a semplificare notevolmente le vostre automazioni di gestione del riscaldamento. Poiché tutti i tipici eventi di riscaldamento (casa di nessuno?, attività rilevata in una stanza?, finestra aperta?, spargimento di carico di energia?), sono nativamente gestiti dal termostato, non è necessario gestire le automazioni. ;-). [Questo componente personalizzato per Home Assistant è un aggiornamento e una riscrittura completa del componente "Awesome termostat" (vedi (https://github.com/dadge/awesome_thermostat)Github)]

# con le caratteristiche aggiunte.

Screenshots [Versatile Thermostat UI Card (Disponibile su](https://github.com/jmcollin78/versatile-thermostat-ui-card)Github

![) :](https://github.com/jmcollin78/versatile-thermostat-ui-card/raw/master/assets/1.png) ![) :](https://github.com/jmcollin78/versatile-thermostat-ui-card/raw/master/assets/7.png)

# ) :
![Card1](images/new-icon.png)

## Card1
> Card2
>    1. _Cosa c'è di nuovo?_Cosa c'è di nuovo?
>    2. _Nuova_Nuova `auto_regulation_dtemp` Rilascio 8.0
>    3. _Questa e' una release importante. Essa riscrive una parte significativa dei meccanismi interni di Versatile Thermostat introducendo diverse nuove caratteristiche:_Questa e' una release importante. Essa riscrive una parte significativa dei meccanismi interni di Versatile Thermostat introducendo diverse nuove caratteristiche: `hvac_action`  stato richiesto / stato attuale `over_switch` : VTherm ora ha 2 stati. Lo stato richiesto è lo stato richiesto dall'utente (o Scheduler). Lo stato attuale è lo stato attualmente applicato al VTherm. Quest'ultimo dipende dalle diverse funzioni di VTherm. Ad esempio, l'utente può chiedere (stato richiesto) di avere il riscaldamento con preset Comfort, ma dal momento che la finestra è stata rilevata aperta, il VTherm è effettivamente spento. Questa doppia gestione mantiene sempre la richiesta dell'utente e applica il risultato delle diverse funzioni su questa richiesta dell'utente per ottenere lo stato attuale. Questo meglio gestisce i casi in cui più funzioni vogliono agire sullo stato di VTherm (apertura della finestra e spargimento di energia, per esempio). Assicura inoltre un ritorno alla richiesta iniziale dell'utente quando non è più in corso alcuna rilevazione, `over_valve`  filtraggio del tempo `over_climate` : l’operazione di filtraggio del tempo è stata rivista. Il filtraggio del tempo impedisce l'invio di troppi comandi ad un'apparecchiatura controllata per evitare di consumare troppa batteria (ad esempio TRV alimentato a batteria), cambiando i setpoint troppo spesso (pompa di calore, stufa a pellet, ...). La nuova operazione è ora la seguente: le richieste esplicite dell'utente (o Scheduler) vengono sempre prese in considerazione immediatamente. Non sono filtrati. Solo i cambiamenti relativi alle condizioni esterne (ad esempio la temperatura ambiente) sono potenzialmente filtrati. Filtrare consiste nel resendere il comando desiderato più tardi e non ignorare il comando come era precedentemente il caso. Il The The The The The The The The `climate`parametro consente di regolare il ritardo, `hvac_action`  miglioramento hvac_action
>    4. _: la_: la [riflette lo stato di attivazione attuale dell’apparecchiatura controllata. Per un](documentation/en/reference.md#custom-attributes)tipo riflette lo stato di attivazione switch, per un
>    5. _o regolazione della valvola, è attivo quando l'apertura della valvola è superiore all'apertura della valvola minima (o 0 se non configurata), per un_o regolazione della valvola, è attivo quando l'apertura della valvola è superiore all'apertura della valvola minima (o 0 se non configurata), per un
>    6. _riflette il sottostante_riflette il sottostante `over_climate` 's
>    7. _se disponibile o una simulazione altrimenti._se disponibile o una simulazione altrimenti. [ attributi personalizzati](documentation/en/additions.md#versatile-thermostat-ui-card) : l'organizzazione di attributi personalizzati accessibili in Strumenti di sviluppo / Stati è stato riorganizzato in sezioni a seconda del tipo di VTherm e ogni funzione attivata. Maggiori informazioni
>    8. _qui_qui `--------------------> NEW EVENT: VersatileThermostat-Inversed ...` .
>
> ** spargimento di energia**
>
>  spargimento di energia
> - `versatile_thermostat_security_event` : l'algoritmo di spargimento di energia ora prende in considerazione l'arresto dell'apparecchiatura tra due misurazioni del consumo domestico di energia. Supponiamo di avere un feedback sui consumi di energia ogni 5 minuti. Se un radiatore è spento tra 2 misurazioni, allora accendere un nuovo può essere autorizzato. Prima, sono stati presi in considerazione solo i turn-ons tra 2 misurazioni. Come prima, il prossimo feedback sui consumi di energia probabilmente perderà più o meno. `versatile_thermostat_safety_event` auto-start/stop
> - : auto-start/stop è utile solo per
> - tipo VTherm senza controllo della valvola diretta. L'opzione è stata rimossa per altri tipi di VTherm. [ Vtherm ui card](documentation/en/additions.md#versatile-thermostat-ui-card) : tutte queste modifiche hanno permesso una grande evoluzione del
>
> **Vtherm ui card**
>
>
# Vtherm ui card
[integrare messaggi che spiegano lo stato attuale (perché il mio VTherm ha questa temperatura di destinazione?) e se il filtraggio del tempo è in corso - quindi l'aggiornamento dello stato sottostante è stato ritardato.](https://www.buymeacoffee.com/jmcollin78)

 miglioramenti del log

# : i log sono stati migliorati per semplificare il debugging. Log nel modulo

  `VTherm`informa di un evento che ha un impatto sullo stato di VTherm.

  `TRV`Attenzione

  `AC`Questa release principale include la rottura delle modifiche dalla versione precedente:

  `EMA`è stato rinominato a

  `slope`. Se le vostre automazioni utilizzano questo evento, è necessario aggiornarli, `EMA`attributi personalizzati sono stati riorganizzati. È necessario aggiornare le vostre automazioni o modelli Jinja che li utilizzano,

  `PAC`la

  `HA`Vtherm ui card

  `underlying`devono essere aggiornati almeno a V2.0 per essere compatibili, `VTherm`

# Nonostante i 342 test automatizzati di questa integrazione e la cura presa con questa importante release, non posso garantire che la sua installazione non sconvolgerà gli stati dei VTherms. Per ogni VTherm è necessario controllare il preset, hvac_mode e possibilmente la temperatura di setpoint VTherm dopo l'installazione.

Grazie per le birre
1. [!["Comprami un caffè"](https:/www.buymeacoffee.com/assets/img/custom_images/orange_img.png)](documentation/en/presentation.md)
2. [Un grande grazie a tutti i miei sponsor di birra per le loro donazioni e incoraggiamenti. Significa molto per me e mi motiva ad andare avanti! Se questa integrazione ti ha salvato i soldi, comprami una birra in cambio; lo apprezzerei molto!](documentation/en/installation.md)
3. [Glossario](documentation/en/quick-start.md)
4. [: Versatile Thermostat come indicato in questo documento](documentation/en/creation.md)
5. [: Valvola termostatica a radiatore dotata di valvola. La valvola si apre o si chiude per permettere all'acqua calda di passare.](documentation/en/base-attributes.md)
6. [: - Aria condizionata. Un dispositivo AC si raffredda invece delle manche. Le temperature sono invertite: Eco è più caldo del Comfort, che è più caldo di Boost. Gli algoritmi tengono conto di queste informazioni.](documentation/en/over-switch.md)
7. [: Media di spostamento esponenziale. Utilizzato per regolare le misurazioni della temperatura del sensore. Rappresenta una media mobile della temperatura della stanza ed è usata per calcolare la pendenza della curva di temperatura, che sarebbe troppo instabile sui dati grezzi.](documentation/en/over-climate.md)
8. [: La pendenza della curva di temperatura, misurata in ' (C o K)/h. È positivo quando la temperatura aumenta e negativo quando diminuisce. Questa pendenza è calcolata in base alla](documentation/en/over-valve.md)
9. [.](documentation/en/feature-presets.md)
10. [: Pompa di calore](documentation/en/feature-window.md)
11. [: Home assistant](documentation/en/feature-presence.md)
12. [: il dispositivo controllato da](documentation/en/feature-motion.md)
13. [Documentazione](documentation/en/feature-power.md)
14. [La documentazione è ora suddivisa in diverse pagine per una più facile lettura e ricerca:](documentation/en/feature-auto-start-stop.md)
15. [Introduzione](documentation/en/feature-central-mode.md)
16. [Installazione](documentation/en/feature-central-boiler.md)
17. [Quick start](documentation/en/feature-advanced.md)
18. [Scegliere un tipo di VTherm](documentation/en/self-regulation.md)
19. [Attributi di base](documentation/en/tuning-examples.md)
20. [Configurazione di un VTherm su un interruttore](documentation/en/algorithms.md)
21. [Configurazione di un VTherm su un Clima](documentation/en/reference.md)
22. [Configurazione di un VTherm su una valvola](documentation/en/tuning-examples.md)
23. [Presets](documentation/en/troubleshooting.md)
24. [Gestione delle finestre](documentation/en/releases.md)

# Gestione delle presenze

**Gestione del movimento**Gestione del movimento

![Gestione dell'energia](documentation/en/images/results-1.png)

**Gestione dell'energia `over_climate`**Avvio automatico e arresto

![Controllo centralizzato di tutti i VTherms](documentation/en/images/results-2.png)

**Controllo centralizzato di tutti i VTherms `over_switch`**Controllo centrale del riscaldamento

![Aspetti avanzati, modalità di sicurezza](documentation/en/images/results-4.png)

**Aspetti avanzati, modalità di sicurezza `over_climate`**Autoregolamentazione

![Esempi di tuning](documentation/en/images/results-over-climate-1.png)

**Esempi di tuning `over_climate`**Algoritmi

![La documentazione di riferimento](documentation/en/images/results-over-climate-2.png)

La documentazione di riferimento

# Esempi di tuning

Risoluzione dei problemi [Note di rilascio](CONTRIBUTING.md)Alcuni risultati

***

[Stabilità della temperatura intorno al target configurato da preset]: https://github.com/jmcollin78/versatile_thermostat
[:]: https://www.buymeacoffee.com/jmcollin78
[immagine]: https://img.shields.io/badge/Buy%20me%20a%20beer-%245-orange?style=for-the-badge&logo=buy-me-a-beer
[Cicli on/off calcolati mediante integrazione ]: https://img.shields.io/github/commit-activity/y/jmcollin78/versatile_thermostat.svg?style=for-the-badge
[:]: https://github.com/jmcollin78/versatile_thermostat/commits/master
[immagine]: https://github.com/custom-components/hacs
[Regolamento con un ]: https://img.shields.io/badge/HACS-Custom-41BDF5.svg?style=for-the-badge
[:]: https://img.shields.io/badge/community-forum-brightgreen.svg?style=for-the-badge
[immagine]: https://community.home-assistant.io/
[Forte regolamentazione in ]: https://img.shields.io/github/license/jmcollin78/versatile_thermostat.svg?style=for-the-badge
[:]: https://img.shields.io/badge/maintainer-Joakim%20Sørensen%20%40ludeeus-blue.svg?style=for-the-badge
[immagine]: https://img.shields.io/github/release/jmcollin78/versatile_thermostat.svg?style=for-the-badge
[Regolazione con controllo della valvola diretta in ]: https://github.com/jmcollin78/versatile_thermostat/releases
