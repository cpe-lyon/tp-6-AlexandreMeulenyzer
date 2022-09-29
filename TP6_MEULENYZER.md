## Exercice 1. Adressage IP (rappels)
| Name  | Hosts Needed | Hosts Available | Unused Hosts | Network Address | Slash | Mask            | Usable Range                | Broadcast    |
|-------|--------------|-----------------|--------------|-----------------|-------|-----------------|-----------------------------|--------------|
| Host1 | 52           | 62              | 10           | 172.16.0.0      | /26   | 255.255.255.192 | 172.16.0.1 - 172.16.0.62    | 172.16.0.63  |
| Host2 | 38           | 62              | 24           | 172.16.0.64     | /26   | 255.255.255.192 | 172.16.0.65 - 172.16.0.126  | 172.16.0.127 |
| Host3 | 37           | 62              | 25           | 172.16.0.128    | /26   | 255.255.255.192 | 172.16.0.129 - 172.16.0.190 | 172.16.0.191 |
| Host4 | 35           | 62              | 27           | 172.16.0.192    | /26   | 255.255.255.192 | 172.16.0.193 - 172.16.0.254 | 172.16.0.255 |
| Host5 | 34           | 62              | 28           | 172.16.1.0      | /26   | 255.255.255.192 | 172.16.1.1 - 172.16.1.62    | 172.16.1.63  |
| Host6 | 33           | 62              | 29           | 172.16.1.64     | /26   | 255.255.255.192 | 172.16.1.65 - 172.16.1.126  | 172.16.1.127 |
| Host7 | 25           | 30              | 5            | 172.16.1.128    | /27   | 255.255.255.224 | 172.16.1.129 - 172.16.1.158 | 172.16.1.159 |

## Exercice 2. Préparation de l’environnement
1/ Ajout d'une interface réseau sur la machine serveur, dont une dans le VLAN ICS_54, même VLAN que la carte réseau de la machine client.  

2/L'interface lo représente le lootback.
![lo](Capture%20d’écran%202022-09-29%20134334.jpg)

3/![désinstall](Capture%20d’écran%202022-09-29%20134609.jpg)

4/![hostname](Capture%20d’écran%202022-09-29%20135249.jpg)


## Exercice 3. Installation du serveur DHCP
1/ ![isc](Capture%20d’écran%202022-09-29%20140649.jpg)

2/ ![ipfixe](Capture%20d’écran%202022-09-29%20143723.jpg)

3/
la durée de bail DHCP est la durée en minutes ou en secondes pendant laquelle un périphérique réseau peut utiliser une adresse IP dans un réseau. L'adresse IP est réservée pour cet appareil jusqu'à l'expiration de la réservation.
première ligne : temps par défaut du bail (120 secondes)
deuxieme ligne : temps max du bail (600 secondes)

4/![écoute](Capture%20d’écran%202022-09-29%20145023.jpg)

5/![service](Capture%20d’écran%202022-09-29%20145157.jpg)

7/
```bash
Sep 29 13:02:37 tpadmin dhcpd[2375]: DHCPDISCOVER from 00:50:56:89:bf:bc via ens192
Sep 29 13:02:38 tpadmin dhcpd[2375]: DHCPOFFER on 192.168.100.100 to 00:50:56:89:bf:bc via ens192
Sep 29 13:02:38 tpadmin dhcpd[2375]: DHCPREQUEST for 192.168.100.100 (192.168.100.1) from 00:50:56:89:bf:bc via ens192
Sep 29 13:02:38 tpadmin dhcpd[2375]: DHCPACK on 192.168.100.100 to 00:50:56:89:bf:bc via ens192
```
DHCPDiscover correspond a la demande en broadcast d'une adresse IP pour le client.  

DHCPoffer correspond a la réponse du serveur au client en unicast,  elle contient une proposition contient l’adresse IP du serveur, l’adresse IP et le masque de sous-réseau, proposées au client.  

DHCPRequest contient l’adresse IP du serveur ayant répondu ainsi que l’adresse qui lui a été fourni précédemment. Cela a pour but de renseigné au serveur que l'adresse IP est maintenant fourni, et donc de ne pas envoyé la même a un autre client.  

DHCPACK fixe l’adresse IP et son masque de sous-réseau au client ainsi que la durée du bail de cette adresse

8/Le fichier contient les différents adresse IP donnée par le serveur aux clients.  
La commande dhcp-lease-list donne les adresses IP actuellement utilisé par des clients sur le réseau donné par le serveur DHCP.

9/ Oui les deux machines peuvent communiqué entre elles :
Du serveur vers le client
```bash
ping 192.168.100.100
PING 192.168.100.100 (192.168.100.100) 56(84) bytes of data.
64 bytes from 192.168.100.100: icmp_seq=1 ttl=64 time=0.220 ms
```

Du client vers le serveur :
![ping](Capture%20d’écran%202022-09-29%20151714.jpg)

