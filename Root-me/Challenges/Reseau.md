# Réseau

---
## FTP - Authentification


https://www.root-me.org/fr/Challenges/Reseau/FTP-Authentification

Le mot de passe se situe au paquet 11.


---
## TELNET - authentification


https://www.root-me.org/fr/Challenges/Reseau/TELNET-authentification

Le mot de passe se situe du paquet 58 à 64.


---
## ETHERNET - trame


https://www.root-me.org/fr/Challenges/Reseau/ETHERNET-trame

Dans un premier temps, il faut décoder la trame de ASCII vers HEX (1-2 digits).

Trame :

```
   00 05 73 a0 00 00 e0 69 95 d8 5a 13 86 dd 60 00
   00 00 00 9b 06 40 26 07 53 00 00 60 2a bc 00 00
   00 00 ba de c0 de 20 01 41 d0 00 02 42 33 00 00
   00 00 00 00 00 04 96 74 00 50 bc ea 7d b8 00 c1
   d7 03 80 18 00 e1 cf a0 00 00 01 01 08 0a 09 3e
   69 b9 17 a1 7e d3 47 45 54 20 2f 20 48 54 54 50
   2f 31 2e 31 0d 0a 41 75 74 68 6f 72 69 7a 61 74
   69 6f 6e 3a 20 42 61 73 69 63 20 59 32 39 75 5a
   6d 6b 36 5a 47 56 75 64 47 6c 68 62 41 3d 3d 0d
   0a 55 73 65 72 2d 41 67 65 6e 74 3a 20 49 6e 73
   61 6e 65 42 72 6f 77 73 65 72 0d 0a 48 6f 73 74
   3a 20 77 77 77 2e 6d 79 69 70 76 36 2e 6f 72 67
   0d 0a 41 63 63 65 70 74 3a 20 2a 2f 2a 0d 0a 0d
   0a
```

Vers HEX (1-2 digits) :

```
siZ`@&S`* AB3tP}>i~GET / HTTP/1.1
Authorization: Basic Y29uZmk6ZGVudGlhbA==
User-Agent: InsaneBrowser
Host: www.myipv6.org
Accept: */*
```

Ensuite, il faut décoder `Y29uZmk6ZGVudGlhbA==` en base64.


---
## Authentification twitter


https://www.root-me.org/fr/Challenges/Reseau/Authentification-twitter

![Image de la trame](img/1.png)


---
## Bletooth - Fichier inconnu


https://www.root-me.org/fr/Challenges/Reseau/Bluetooth-Fichier-inconnu

Ouvrir le fichier dans Wireshark, puis naviguez dans `Wireless` et `Equipements Bluetooth`, ici sera inscrit l'adresse MAC et le nom du téléphone. Ensuite, il faut juste suivre la suite des instructions.



---
## CISCO - mot de passe


https://www.root-me.org/fr/Challenges/Reseau/CISCO-mot-de-passe

On trouve dans le fichier du challenge les lignes suivantes :

```
username hub password 7 025017705B3907344E 
username admin privilege 15 password 7 10181A325528130F010D24
username guest password 7 124F163C42340B112F3830
```

En déchiffrant les mots de passe avec le "weak reversible algorithm", on obtient les mots de passe suivant pour hub, admin et guest :

```
6sK0_hub
6sK0_admin
6sK0_guest
```

Tout logiquement, le mot de passe de `enable secret 5 $1$p8Y6$MCdRLBzuGlfOs9S.hXOp0.` est trouvable facilement.



---
## Dns - transfert de zone


https://www.root-me.org/fr/Challenges/Reseau/DNS-transfert-de-zone

Il suffit d'éxécuter la commande `dig @challenge01.root-me.org -p 54011 axfr ch11.challenge01.root-me.org` et la clé secrète sera inscrite en réponse à la commande.



---
## IP - Time To Live


https://www.root-me.org/fr/Challenges/Reseau/IP-Time-To-Live

La réponse est située au packet 71.



---
## SIP - Authentification


https://www.root-me.org/fr/Challenges/Reseau/SIP-Authentification

On a 3 lignes qui font référence aux 2 mêmes IPs. La mention REGISTER dans la première ligne laisse penser qu’il s’agit de l’enregistrement d’un utilisateur. La structure de chaque ligne montre des champs séparés par des guillemets doubles. On peut facilement voir que l’avant dernier champ de chaque ligne correspond à une méthode de codage.
On voit ainsi que l’enregistrement de la première ligne à été fait avec le mot de passe (dernier champ) en clair (PLAIN).