### Multicast UDP  

>Es tracta d’adreces a les quals es poden fer subscripcions.  
>Són adreces que no pertanyen a cap dispositiu concret, però que són controlades per certs dispositius intermedis que anomenem encaminadors o routers. Aquests dispositius poden rebre la petició de qualsevol 
>dispositiu d’afegir la seva adreça IP a la multidifusió de qualsevol paquet dirigit a l’adreça multicast. 
>És a dir, que el router, en detectar l’enviament d’informació dirigida a una adreça broadcast controlada per aquest dispositiu replicarà el paquets
>rebuts a totes les IP associades a l’adreça multicast  

Com veieu hi ha un element de subscipció, i per tant el nostre client
ha de tenir un mètode per poder fer aquesta subscripció i un altre
per abandonar-la (**joinGroup i leaveGroup**). Aquest mètodes pertanyen
a un socket que en aquest cas és instància de MulticastSocket.

```java
MulticastSocket socket = new MulticastSocket(port);  
socket.joinGroup(multicast_ip);  
    // bucle de comunicació  
    // tasca que desenvolupa el client  
    // usant DatagramPacket  
socket.leaveGroup();  
```
El servidor per la seva banda té un bucle molt senzill on només cal preparar
les dades que vol enviar i enviar.  

Classes involucrades en aquest exercici:  
[`SrvVelocitats.java`](SrvVelocitats.java) Servidor  
[`ClientVelocimetre.java`](ClientVelocimetre.java) Un client que fa una tasca  
[`Velocitat.java`](Velocitat.java) Classe per alliberar de feina i no barrejar reponsabililtats en la tasca de comunicació  

### Exercici:
Escriu el codi de `ClientVelocimetre.java` per tal de connectar-se al servidor multicast i que cada 5 dades recollides del servidor
el client ens mostri la velocitat mitjana que porta en aquell moment.
