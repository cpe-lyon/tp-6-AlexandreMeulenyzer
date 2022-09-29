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

4/

