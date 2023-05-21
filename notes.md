## DNS (UDP vs TCP)

Il protocollo DNS (Domain Name System) può utilizzare sia TCP (Transmission Control Protocol) che UDP (User Datagram Protocol) come protocolli di trasporto, a seconda delle circostanze e delle esigenze.

Di solito, la maggior parte delle richieste DNS viene effettuata tramite UDP. UDP è un protocollo di trasporto leggero e veloce che offre una comunicazione senza connessione, adatto per le query DNS che richiedono una risposta rapida. La porta standard per le comunicazioni DNS tramite UDP è la porta 53.

Tuttavia, in alcuni casi, le risposte DNS possono superare la dimensione massima di un singolo pacchetto UDP (limitato a 512 byte o 4096 byte in alcune implementazioni). Quando ciò accade, DNS può passare automaticamente all'utilizzo di TCP per la trasmissione delle informazioni. TCP offre una comunicazione affidabile e consente la trasmissione di dati più voluminosi, ma è un po' più pesante rispetto a UDP a causa della sua natura basata su connessione. La porta standard per le comunicazioni DNS tramite TCP è anche la porta 53.

Quindi, in sintesi, la maggior parte delle comunicazioni DNS avviene tramite UDP per la sua leggerezza, ma in caso di risposte più grandi, DNS può commutare a TCP per garantire una consegna affidabile dei dati.




## Pseudo-header (UDP)

Lo pseudoheader è un componente utilizzato nel calcolo del checksum (somma di controllo) del segmento IP o datagramma UDP. Serve a garantire l'integrità dei dati durante la trasmissione.

Nel caso specifico del protocollo UDP, il calcolo del checksum coinvolge sia l'intestazione UDP che i dati effettivi del payload. Tuttavia, per rendere il calcolo del checksum più affidabile e accurato, viene utilizzato uno pseudoheader, che contiene alcune informazioni estratte dall'intestazione IP. Lo pseudoheader include i seguenti campi:

- Indirizzo IP di origine
- Indirizzo IP di destinazione
- Zero (riservato per allineamento)
- Protocollo (in questo caso, UDP)
- Lunghezza totale dell'intestazione UDP e dei dati

L'integrazione dello pseudoheader nel calcolo del checksum garantisce che eventuali modifiche o errori nell'intestazione IP vengano rilevati, contribuendo a fornire una maggiore sicurezza contro la corruzione dei dati durante la trasmissione.

In sostanza, lo pseudoheader consente di aggiungere ulteriori informazioni relative all'intestazione IP al calcolo del checksum del segmento UDP, migliorando la capacità di rilevare errori o modifiche nell'intestazione IP e garantendo un livello di integrità aggiuntivo nella comunicazione.




## Pseudo-header (TCP)

The TCP pseudoheader is not actually located anywhere in the TCP segment. It is a logical construct that is used to calculate the checksum of the TCP segment. The pseudoheader is created by concatenating the following fields:

* Source IP address
* Destination IP address
* Protocol type (TCP = 6)
* TCP segment length

The checksum is then calculated over the pseudoheader and the TCP segment. If the checksum is not zero, then the TCP segment is discarded.

The pseudoheader is a necessary part of the TCP checksum calculation because the TCP checksum does not include the IP header. This is because the IP header is not part of the TCP segment, and it can be modified by routers and other network devices.

The pseudoheader ensures that the TCP segment has not been corrupted by ensuring that the IP header has not been modified. This is important because the IP header contains information that is needed to route the TCP segment to its destination.

The pseudoheader is a simple but effective way to ensure the integrity of TCP segments. It is a fundamental part of the TCP protocol and it is used by all TCP implementations.

---

The UDP pseudoheader is similar to the TCP pseudoheader, but it has a few key differences. The UDP pseudoheader consists of the following fields:

* Source IP address
* Destination IP address
* Protocol type (UDP = 17)
* UDP length

The main difference between the TCP and UDP pseudoheaders is the protocol type field. The protocol type field in the TCP pseudoheader is 6, while the protocol type field in the UDP pseudoheader is 17. This difference is because TCP and UDP are different transport layer protocols.

Another difference between the TCP and UDP pseudoheaders is the length field. The length field in the TCP pseudoheader includes the length of the TCP header and the TCP data, while the length field in the UDP pseudoheader only includes the length of the UDP data. This difference is because UDP does not have a header.

The TCP and UDP pseudoheaders are both used to calculate the checksum of their respective protocols. The checksum is used to ensure that the protocol segment has not been corrupted in transit.




## Does TCP read IP header?

Yes, TCP does read the IP header. The IP header contains the source and destination IP addresses, which are used by TCP to establish a connection with the remote host. The IP header also contains the protocol type, which tells TCP that the data is encapsulated in a TCP segment.

TCP uses the information in the IP header to demultiplex the data to the appropriate application. For example, if a web browser is listening on port 80, and it receives an IP packet with a destination port number of 80, then TCP will deliver the data to the web browser.

TCP also uses the IP header to calculate the checksum of the TCP segment. The checksum is used to ensure that the TCP segment has not been corrupted in transit.

TCP reading the IP header is an essential part of how the TCP/IP protocol works. It allows TCP to establish connections with remote hosts, demultiplex data to the appropriate applications, and ensure the integrity of data in transit.
