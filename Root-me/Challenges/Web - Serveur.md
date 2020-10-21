# Web - Serveur
---
## HTML - Code source


https://www.root-me.org/fr/Challenges/Web-Serveur/HTML-Code-source<br/>

Il suffit d'inspecter le code source et le mot de passe sera dans un commentaire avant la fin du body.<br/>

---
## Mot de passe faible


https://www.root-me.org/fr/Challenges/Web-Serveur/Mot-de-passe-faible<br/>

Dans ce challenge, il suffit juste de tester des combinaisons basiques qu'il est possible de retrouver dans des logiciels, base de données, comptes lorsqu'ils sont fournis aux utilisateurs et que les utilisateurs ne changent pas ces mot de passe d'usine.

---
## SQL injection


https://www.root-me.org/fr/Challenges/Web-Serveur/SQL-injection-authentification<br/>


La commande `--` permet de bypasser le mot de passe, il faut donc la mettre à la suite du login.<br/>
Il suffit de rentrer dans le login `admin' --` et n'importe quel mot de passe dans la case mot de passe.<br/>
Après avoir fait cela, le site considère la connexion comme établie, il suffit donc d'inspecter la case du mot de passe et d'en prendre la valeur.<br/>