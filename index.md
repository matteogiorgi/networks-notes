# [Appunti reti](https://github.com/matteogiorgi/appunti-reti)

- [Elearning](https://elearning.di.unipi.it/course/view.php?id=312)
- [Slides](https://mega.nz/folder/kxAFjTya#DdpylJrqtSZ-q8tG5KCSZg)
- [Notes](notes.md)


## Programma

- introduzione
    - LAN
    - WAN
    - commutazione di pacchetto/circuito
    - ISP
    - metriche
        - larghezza di banda
        - velocità di connessione
        - throughput
        - latenza
            - elaborazione (trascurabile)
            - accodamento (trascurabile)
            - trasmissione
            - propagazione
- modello ISO/OSI
- stack TCP/IP
- livello applicazione
    - socket
    - URI/URL
    - HTTP
        - persistente/non persistente
        - pipeline
        - formato messaggi richiesta/risposta
        - metodi
        - caching
        - cookies
    - TELNET
    - SMTP
        - formato messaggi
        - MIME
        - accesso alla mail
    - POP
    - IMAP
    - DNS
        - spazio dei nomi
        - name server
        - query iterative/ricorsive
        - record DNS
    - FTP
        - control connection
        - data connection
- livello trasporto
    - servizio orientato/non orientato alla connessione
    - mutiplexing/demultiplexing
    - porte riservate
    - TCP
        - formato del segmento TCP
        - numero sequenza e riscontro
        - instaurazione e chiusura connessione (3-way handshake)
        - trasferimento dati affidabile
        - finestra trasmissione/ricezione
        - controllo di flusso
        - controllo congestione
        - TCP Tahoe
        - TCP Reno
    - UDP
        - formato del datagramma UDP
        - pseudoheader
        - checksum
        - TCP vs UDP
- livello rete
    - IP
        - modello datagram
        - formato del pacchetto IP
        - frammentazione
        - indirizzamento IP
        - addressing flassfull/classless
        - subnet mask
        - aggregazione degli indirizzi
        - forwarding diretto/indiretto
        - NAT
    - DHCP
    - ICMP
        - ping
        - traceroute
    - architettura router
        - control plane/data plane
        - routing decentralizzato/centralizzato
        - algoritmi di routing
        - distance vector/link state
        - routing gerarchico
        - sistemi autonomi (routing inter-AS)
    - BGP
    - RIP
    - OSPF
    - IPv6
    - dual stack
    - IPv4 tunneling
- livello collegamento
    - protocollo MAC
    - ARP
    - ethernet
    - dispositivi di interconnessione (switch, hub)
    - VLAN
- applicazioni p2p
    - reti p2p
    - bittorrent
- sicurezza
    - cifratura
    - firma digitale
    - IPSec
    - SSL/TLS




## Orali 10 giugno

### Orale 1 - 11:00 (18)

- come mai viene perso un pacchetto
- cos'è best effort service
- cosa significa aggiornale la finestra di ricezione
    - dove sta il valore della finestra di ricezione
    - il mittente nn sa a priori quanto spazio c'è, quindi come fa a sapere quanto vale la finestra di ricezione
    - byte sonda?
- cos'è fuori dal controllo del mittente
    - chi consuma i dati dal buffer (come fa il buffer a svuotarsi)
    - il mittente non sa quando il livello applicativo andrà a consumare i dati
- cosa si intende per forewarding diretto e indiretto
    - in caso di forwarding indiretto quali sono gli indirizzi di destinazione
    - indirizzo MAC, indirizzo router, indirizzo destinatario
- com'è fatta la tabella di inoltro di un router (quali sono i campi)
- cos'è la tabella di inoltro di un router
- chi decide quali sono i valori da mettere nella tabella del router (i protocolli di routing)
- EGP a cosa serve
- quale sono le differenze tra EGP e BGP


### Orale 2 - 11:50 (23)

- quando si va a modellare il ritardo end2end, quali sono i vari componenti di ritardo (trasmissione, propagazione, accodamento, elaborazione)
- cos'è il ritardo di propagazione
- dove si verifica il ritardo di accodamento
- a cosa è dovuto il ritardo di elaborazione
-  come si fa il controllo di flusso (con la finestra)
-  differenze tra il controllo di flusso e il controllo di congestione
- com'è fatto e cosa fa uno switch
- com'è fatto un recor DNS


### Orale 3 - 12:10 (24)

- come si calcola il ritardo di trasmissione
- cos'è il ritardo di propagazione
    - è riferito al pacchetto o al singolo bit
- cos'è una VLAN
    - come si fa a implementare la VLAN (abbiamo visto un modo = con gli switch)
    - serve per limitare il dominio di broadcast: dare esempi di ...
    - l'indirizzo IP è nel payload (ma di cosa?)
    - è incapsulato in un frame (ma cosa?)
- come fa un client a conoscere il suo indirizzo IP
- DHCP è un protocollo di che livello
    - che protocollo di trasmissione usa (UDP)
    - il messaggio DHCP a chi viene mandato, c'è un indirizzo preciso o no (all'indirizzo di broadcast)
- cos'è e come funziona il protocollo RIP
    - è usato per calcolare la distanza solo di nodi non adiacenti o no
    - dai esempio di un caso dove si arriva ad avere un "count infinity"
        - qual'è un modo per cercare di liìmitare questi casi (aggiornare gli adiacenti?)


### Orale 4 - 12:35 (28)

- esercizio sul livello di rete (nell'esercizio bisognava identificare 6 sottoreti?)
    - a cosa serve e come funziona la maschera di rete
    - 150.210.12.12.24 che informazioni mi da
- cosa fa `traceroot` e come si implementa (una strategia è quella di mandare dei messaggi di ping - che si fa con l'ICMP)
- com'è fatta la finestra di trasmissione del TCP
- e se anche il valore della finestr di congestione che succede (prendo il minimo)
- cos'è il NAT


### Orale 5 - 13:00 (30L)

- cosa significa metodo safe HTTP e fai quanche esempio
- cosa fa il POST
    - quale sarà l'URI della sottorisorsa creata dal server
- com'è il metodo DELETE (è idempotente)
- TCP Reno con controllo di congestione: come evolve la finestra di congestione al trascorrere del tempo
- a cosa serve il controllo di congestione
- UDP non ha ne controllo di flusso ne controllo di congestione, quindi in che applicazioni viene usato
- com'è fatta la gerarchia dei server DNS
- a livello di rete quali sono le funzioni di piano di controllo e di piano dati, in cosa differiscono
- abbiamo visto algoritmi di routing per un sistema distribuito, in che altro modo si può fare
    - quali sono i pro e i contro di avere un approccio centralizzato
    - quale vantaggio ci può essere nell'avere più punti di distribuzione


### Orale 6 - 13:15 (30)

- perchè può essere non buono avere un client FTP dietro un NAT (ma non sono sicuro)
    - vedi le specifiche del protocollo FTP
- a cosa servono le VLAN
    - a cosa serve indivuare e raggruppare i sottogruppi
- come fa uno switch a mandare tot frame a questi e non a quest'altro (con ARP chiede l'indirizzo MAC e glieli invia - si ouò fare anche porte e tag)
- come funziona il BGP


### Orale 7 - 13:35 (19)

- come funziona l'handshake TCP
- differenze tra HTTP1.0 e HTTP1.1
    - considerando l'hadshake, quanto guadagno in tempo (1RTT)
- livelo rete e indirizzamento con/senza classi: perchè siamo passati a qualle senza classi
- cos'è OSBF
    - come fa un nodo a conoscere al titopogia della rete
- com'è fatta la tabella di inoltro di un ruoter
- cosa si intende per forewarding diretto e indiretto a livello di rete
- a cosa serve l'indirizzo di MAC
    - come fa l'host a inviare un datagramma al router (usa l'indirizzo MAC del router)




## Orali 29 giugno

### Orale 1 - 11:05 (30)

- come funziona la chiusura della connessione TCP
- al livello 3 cos'è `traceroot`  e come viene implementato
    - implementazione Linux
    - implementazione Windows (che tipo di pacchetto viene usato)
    - cosa fa `traceroot` per ovviare alla perdita dei pacchetto
- come mai sono state introdotte le VLAN e a cosa servono
    - dato l'esempio scritto, come può lo switch gestire le VLAN, ovvero sapere quale host appartiene a quale VLAN (abbiamo visto un modo particolare)
    - a cosa serve il *tag*


### Orale 2 - 11:30 (30L)

- domanda sull'inoltro del compito
    - come viene in dettaglio l'inoltro verso l'indirizzo `80.20.40.2`
- il DNS come si posizionerebbe nell standard ISO-OSI (applicativo)
- il livello applicativo che informazioni passa al livello trasporto
    - #porta
- TCP è con connessione, invece senza connessione di cosa si parla (UDP)
- come si fa ad assegnare un indirizzo IP ad un host (con il DHCP)
    - l'assegnazione dell'indirizzo quanto dura
    - attenzione che l'host può rinnovare
- cos'è il *control plane* (siamo nel router)
- cos'è IPsec (trasporto e tunnel)


### Orale 3 - 11:50 (22)

- domanda DNS del compito
    - confusione sul mail server
- cos'è BGP
    - eBGP vs iBGP
- cos'è il controllo di flusso in TCP
    - il mittente di cosa se ne fa del campo finestra


### Orale 4 - 12:10 (~)

- domanda sulla richiesta d'inoltro del compito
    - nel caso specifico è un'inoltro diretto o indiretto
    - come fa il router R a inoltrare un pacchetto a questo next-hop
        - cosa succede a livello collegamento, ovvero come fa il datagramma ad arrivare al next-hop
        - come si fa a cercare il MAC
        - come funziona ARP
        - come fa l'host, se non trova il MAC nella tabella ARP


### Orale 5 - 12:30 (~)

- come funziona l'algoritmo *distance-vector*
- a cosa serve ARP e conme funziona
- come funziona uno switch
    - a cosa serve la tabella


### Orale 6 - 12:40 (~)

- domanda sullo switch del compito
- come fa lo switch a costruirsi la tabella
- a cosa serve ARP e come funziona
- come fa il router a capire se fare inoltro diretto (stessa sottorete) o indiretto (diversa sottorete)
    - come fa B a sapere che A non è nella stessa sottorete
    - qual'è l'indirizzo di rete di B


### Orale 7 - 12:55 (19)

- dalla domanda dello scritto, a cosa servono i seguenti metodi HTTP
    - qual'è il metodo che restituisce l'identificazione di una risorsa (PUT)
    - la POST a cosa serve
- altra domanda dello scritto (qualcosa su `ACK` e `SINACK`)
- cosa significa che il TCP è *fair*
- cosa si intende per forwarding diretto e indiretto a livello di rete
- fai un disegno esemplificativo di una sottorete che mostri forwarding diretto e indiretto
- come fa A a conosceer l'indirizzo MaAC di R
- cos'è BGP
- come funziona l'algoritmo *distance-vector*
- cos'è il controllo di congestione in TCP


### Orale 8 - 14:05 (23)

- domanda sulla rete del compito
- domanda sulla sicurezza? del compito
- come funziona l'algoritmo *distance-vector*
- algoritmi Inter-AS: RIP e OSDR
    - cosa si usa su reti grandi: RIP o OSBF
    - come è possibile inviare un datagramma tra due sottoreti di aree differenti
- come è implementato in TCP il trasferimento dati affidabile
- il transmission-timeout a cosa serve e come viene calcolato
- perchè l'RT stimato non è direttamente quello misurato
- cos'è uno switch
    - come fa uno switch a inoltrare sul giusto collegamento i frame gli arrivano
    - come fa lo switch a memorizzare la *tabella di commutazione*
    - quali sono le informazioni contenute nella tabella


### Orale 9 - 14:40 (23)

- domanda dello scritto
    - che succede se mando un FIN
    - cosa significa che il TCP tende ad avere un comportamento equo
        - che succede quando ho 2 TCP che condividono un collegamento
        - quali sino i meccanismi con cui il TCP invia i dati al destinatario
        - cosa fa invece il controllo di congestione
        - il problema della congestione è solo livello collegamento o anche sul router
        - come funziona il controllo di congstione con il TCP-RENO
        - come viene aumentata la finestra di congestione all'arrivo di un `ACK` non duplicato
- livello applicativo: come funzione il protocollo FTP
    - la data connection chi la apre?
    - cosa sono le modalità attiva e passiva
- cos'è un NAT




## Orali 20 luglio

### Orale 2 - 09:45 (25)

- esercizio della tabella d'inoltro dello scritto
    - qui il forewarding è diretto o indiretto
    - cosa si intende per forewarding diretto/indiretto
- cosa sono le fasi di *slow start* e *congestion avoidance*
    - come funziona *TCP-Reno*
    - quale tipo di evento di perdita (si parla dei 3 riscontri)
    - la finestra di congestione cambia alla ricezione qualsiasi tipo di riscontro ricevuto?
        - se il riscontro ricevuto è un *timeout*, che succede? \
          `congestion_window=20; arriva timeout`
- cos'è uno switch e come funziona
    - fare fintraggio (non ho capito bene la domanda)


### Orale 3 - 10:15 (27)

- domanda su esercizio TCP dello scritto
- distance vector e algoritmi di routing
- con un sistema autonomo ... si usa ...
- servizio di trasmissione affidabile
    - quando viene impostato il *timeout*?
- come funzina `traceroot`


### Orale 4 - 10:40 (23)

- esercizio IP dello scritto
- cosa si intende per *multiplexing/demultiplexing* a livello trasporto
    - quali sono le informazioni di una soket connessa (indirizzo IP e #porta)
    - che differenza c'è tra un servizio orientato alla connessione e uno non orientato alla connessione
- come è implementato il controllo di flusso in TCP
    - che succede se il client ha inviato dei byte che non sono stati riscontrati, ovvero come usa l'informazione della finestra di ricezione
- c'è il NAT, come funziona e cosa se ne fa il router delle informazioni del NAT
- dentro una rete NAT, solo un processo alla volta può comunicare con il server?


### Orale 5 - 11:00 (30)

- esercizio rete con gli switch dello scritto
- com'è fatto un router
    - quando si verifaca accodamento?
- cosa sono *piano di controllo centralizzato/decentralizzato*
- a cosa servonon e cosa sono i *sistemi autonomi*
- quali considerazioni posso fare quando ho un client UDP che vuove comunicare con una rete con NAT
- cosa sono le VLAN


### Orale 6 - 11:35 (30)

- esercizio BGP e router di frontiera dello scritto
- diffferenza tra una query dichiarative e una ricorsiva nel DNS
- il name-server è obbligato a risolvere la query in modo ricorsivo?
- cos'è IPSec
    - in *tunnel-mode* tutto il pacchetto viene cifrato (compreso l'header), quindi come fa il TCP a inoltrare il pacchetto → viene aggiunto un nuovo header
- perchè ci sono applicazioni UDP se TCP offre così tanti vantaggi
    - quant'è il ritardo nell'usare il TCP invece di UDP (`1 rtt`)
    - UDP può perdere dati, quindi che succede se a livello di DNS perdo la richiesta \
      poi chi la rimanda?


### Orale 7 - 12:00 (25)

- esercizio dello scritto
- differenza tra forewarding diretto e indiretto
    - come fa lo strato IP a fare in modo che il datagramma arrivi al router della rete giusta
- cos'è il MIME
- cos'è il NAT


### Orale 7 - 12:00 (22)

- esercizio sulla tabella d'inoltro dello scritto
- cosa fa il router per inoltrare verso l'host
    - ovvero  cosa succede a livello rete e collegamento
    - quali sono gli indirizzi collegamento e indirizzi rete (sorgente e destinazione)
    - come fa un certo ruter a conoscere l'indirizzo MAC di un'altro router (usa ARP)
    - come funziona ARP e cosa c'è nel messaggio di richiesta
- cos'è il NAT
    - come mai non è sufficiente modificare l'IP ma serve anche cambiare la porta sorgente
- come avviene la chiusura della connessione TCP
- come si fa a chiedere la chiusura della connessione TCP
- quand'è che si può ricevere un riscontro duplicato (dare esempio)
- cosa si intende per metodi *safe* e *idempotenti*
    - cos'è la POST (safe/idempotente) e cosa fa
    - cos'è la PUT (safe/idempotente) e cosa fa
    - che differenza c'è tra PUT e POST


### Orale 8 - 15:50 (20)

- esercizio sui main-server dello scritto \
  *quali tra i seguenti è un main-server autorevole*
- come si risolve una query DNS
    - come fa `mailserver.it` chi contattare per poter risolvere `unipi.it`
    - cos'è il local-mailserver (è al di fuori della gerarchia)
    - quali sono i tipi di record DNS che abbiamo visto
    - cos'è l'associazione nameserver
    - il record DNS di tipo NS cosa conterrà nei campi *value* e *???*
- come funziona il controllo di flusso in TCP e come viene implementato
- cos'è il NAT
    - che succede se un'host dall'esterno volesse contattare un host dentro la rete NAT
- come fa un host ad acquisire il proprio indirizzo IP
- DHCP che tipo di protocollo è (dove è messo il messaggio DHCP)
    - serve UDP perchè il messaggio va inviato in broadcast
- come avviene la chiusura del messaggio TCP


### Orale 9 - 16:20 (29)

- esercizio sul servizio DNS dello scritto
- cosa si intende per server host-alising
- cosa è successo di importante nel passaggio dal protocollo `HTTP 1.0` a `HTTP 1.1`
    - quali sono i vataggi di `HTTP 1.1` (risparmio di risorse)
    - che vantaggio ha avere `HTTP 1.1` a livello TCP
- a cosa serve la fase di *fast recovery* in TCP Reno
- cosa si intende *ALOHA* e *Slotted ALOHA*
- come funziona l'algoritmo *Distance Vector*
    - come si applica la formula di Bellman-Ford




## Orali 26 luglio

### Orale 2 - 10:00 (26)

- descrivi il processo lato server e le scelte principali
    - è sicuro di cotrollare che legge tutti i byte?
- che tipo di thread ha scelto
- quali sono le strutture dati che ha scelto
- le singole operazioni sono atomiche, perchè il blocco di operazioni non lo è
    - potrebbe essere un problema?
- nell'operazione di registrazione, c'è necessità di garantire la consistenza?
- cos'è una `ReadWriteLock`
- hai usato un `ChachedTreadpull`: cos'è un *treadpull* e come si configura
    - cosa succede se arrivassero più task rispetto hai tread possibili
    - quali tipi di code possono essere usate
    - sulla terminazione di un *tread* (`Shutdown`/`ShutdownNow`)
- cos'è un'interfaccia REST
- a cosa serve la `POST`


### Orale 3 - 10:25 (23)

- controllo errore orale precedente
- cos'è una `ConcurrentHashMap`
    - ci sono metodi particolari?
    - perchè non conviene usare una semplice `Map` con un blocco sincronizzato? (bloccherei l'intera `Map`)
- come hai implementato la registrazione
- cos'è una *condition variable*
    - fai un esempio di utilizzo
- se avessi usato un `Selector`, cosa sarebbe cambiato (non ho capito il contesto)
    - cos'è e come funziona un `Selector`
    - come avresti fatto il server con il `Selector`
        - quanti e quali canali registra


### Orale 4 - 10:45 (26)

- il thread che legge è lo stesso che scrive, come mai?
- come hai fatto la registrazione dei canali? (con una coda)
- quale scelte hai fatto per la gestione della concorrenza
- faccia vedere la `DeletePost`
    - c'era bisogno di renderla mutuamente esclusiva?
    - cosa succede se dovessi cancellare due volte lo stesso post
      (il post viene tolto atomicamente quandi, se qualcuno va a vedere, non lo trova più)
- come hai implementato il servizio remoto
- come hai implementato la `Register`
- come si fa in Java ad implementare la comunicazione *multicast*
- cos'è e a cosa serve il costrutto *try-with-resources*
- cos'è lo standard RMI
    - come funziona la `callback`


### Orale 5 - 11:11 (19)

- hai usato un `Selector`
    - lato server, quanti thread ci sono
    - perchè qui hai messo un blocco `syncronized` (superfluo)
- quali altri meccanismi di sincronizzazione hai usato nel progetto
- mi mostri l'implementazine della registrazione alla `callback`
- cosa sonon i *monitor*
- come si fa ad interrompere un thread


### Orale 6 - 11:30 (19)

- domanda sulla relazione
- quali sono le strutture dati principali lato servere e le soluzioni per garantire concorrenza
- hai usato molti metodi `syncronized`, come avresti potuto fare in modo più efficiente (`ReadWriteLock`)
    - come funziona la `ReadWriteLock`
- nelle operazioni RMI c'è bisogno di usare meccanismi di sincronizzazione?
- fai un esempio dove due client si registrano con lo stesso account (?)
- quali sono le operazioni che possono ... (NIO `Selector`)
    - cosa si fa lato servere per accettare le richieste di connessione
    - quante `ServerSocketChannel` servono?
    - come fa un server a capire che ci sono più client a inviare richieste?


### Orale 7 - 12:00 (26)

- mostra l'implementazione del `WriteThread`
    - avresti potuto cambiare il canale da *bloccante* a *non-bloccante*
- che strutture dati hai utilizzato per il server
    - che cosa hai fatto per gestire la concorrenza?
- come gestisci la `Rewind` (?)
- mostra la chiamata al servizio remoto
- cos'è un *threadpull*
- come funziona una `LinkedListQueue`
- che differenza c'è tra una variabile *volatile* e *atomica*
- cos'è la *object serialization* in Java


### Orale 8 - 12:25 (26)

- come mai hai fatto una gui per il server e non per il client
- scelte principali del progetto lato servere (struttura e concorrenza)
- come mai sul serverRMI ...
- come funzina e come si risolvono le *deadlock*
    - si può anche usare il blocco syncronized per mettersi in attesa
- come funzione REST e le interfacce remote (?)
    - avresti potuto implementare il server con REST?
    - e la POST? (si può usare il body del messaggio)


### Orale 9 - 12:50 (18)

- come mai hai scelto queste 4 concurrent hashmap per gestire i dati
- sul serverRMI co sono problemi di consistenza da gestire?
- mostra la chiamata del servizio *Random*
- `HashMap` syncronized vs `ConcurrentHashMap`
    - come funzionando le lock nella `ConcurrentHashMap`, quanti thread possono accedere in lettura/scrittura
    - come mai la `ConcurrentHashMap`
- cos'è un monitor
    - ci sono altri modi di gestire le concorrenze
- se avessi usato NIO+`Selector` come sarebbe stata la struttura del server
    - spiega meglio come funzionano `SocketChannel` e `ServerSocketChannel`
    - se registri in `ServerSocketChannel` sul `Selector`


### Orale pomeriggio (14:00)

#### Teoria (26)

- a cosa serve e come funziona il controllo di congestione
- come mai è stata differenziata la ...
- come fa il destinatatio a mandare gli ACK duplicati
- qual'è lo scopo di ICMP e come viene usato per gestire il *Payload*
    - in Windows l'implementazione di `Traceroute` è diversa
- cos'è una VLAN

#### Laboratorio (25)

- spiega quali strutture dati hai utilizzato e come
- come funziona la registrazione (?)
    - come mai c'è bisogno di mettere le *Lock*
- invece di creare 4 `Lock`, avresti potuto fare 1 sola coppia di `ReadWriteLock`?
- domanda sui *syncronized*
- cos'è il costrutto *try-with-resources*
    - cosa succede se viene lanciata un'eccezione
    - è la stessa cosa utilizzare il blocco try e poi chiudere lo `Stream` nel `final`?
- cos'è il `Selector`
- come mai hai optato per la ... (?)
