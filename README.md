
# CNAM TP1 : Scan de Ports

Le but de ces Travaux Pratiques est de manipuler les concepts de base couverts en cours.

Nous allons écrire un scanner de ports en C. Il va s'agir de réaliser un programme simple manipulant des sockets TCP/IP.

## Resultats

Ces TPs sont notés : prière de m'envoyer vos résultats (source code, Makefiles, réponses à chaque question) sous 1 semaine, sur mon email du CNAM.

## Scanner TCP/IP

On cherche à écrire un scanner de ports en C.

La programmation de sockets en C manipule directement les objets utilisés par le noyau (appels systeme) et est plus bas niveau (id est: plus complexe) que via des langages de plus haut niveau.

Voici un bon tutorial, très complet, concernant la programmation de sockets en C : https://beej.us/guide/bgnet/html/

### Pre-requis : installer un compilateur C et ses dependances sous Linux

Sous les environements fondés sur Debian, tels qu'Ubuntu, il faut installer les packets suivant: build-essential

Ecrire un fichier Hello World ainsi que son Makefile, et vérifier que le compilateur C fonctionne effectivement.

### Compilation d'un client C

Telecharger le code d'un client TCP simple ici: https://beej.us/guide/bgnet/examples/client.c . Vous pouvez utiliser les commandes curl ou wget.

Modifier le port destination dans le client.c afin de se connecter au port 80.

Ecrire un Makefile afin de compiler client.c.

Tester le client compilé en tentant de se connecter au port 80 de Google. Que se passe t'il ? Pourquoi ?

Utiliser la command strace (voir man strace) pour suivre les appels systèmes utilisés succèssivement par votre client TCP pour se connecter a Google. Quel est le dernier ? Pourquoi bloque t'il ?

Modifier le code du client pour effectuer une requete HTTP GET et afficher le résultat (voir par exemple ce lien pour la construction d'une requete GET: https://www.ibm.com/docs/en/cics-ts/5.3?topic=samples-example-http-get-request-using-query-string).  Vous aurez besoin d'utiliser l'appel systeme send(). Utiliser le manuel Linux et/ou le Beej tutorial pour déterminer comment utiliser cet appel système.

Que se passe t'il ? Pourquoi ?

Quelle est l'IP de google.com ? Y en a t'il plusieurs ? Pourquoi ?

Le port 80 de Google est il ouvert ?

### Ecriture d'un scanner de ports

Modifier le code de client.c (le nommer scanner.c) pour se connecter au port 80 et afficher un message différent suivant que la connection est réussie (port ouvert) ou non (port fermé).


Modifier votre code afin d'effectuer ces operations sur les ports 1 à 1024.

Scanner les ports de gmail.google.com.

Quels sont les ports ouverts ?

### Ajout des noms des services

Modifier le code de scanner.c pour afficher le nom des services associès aux ports ouverts (utiliser le fichier /etc/services).

Que pensez vous de la vitesse de scan ?


### SYN scans

Lire https://nmap.org/man/fr/man-port-scanning-techniques.html et https://nmap.org/book/synscan.html

On cherche à augmenter la vitesse de scan.

Par default, quel est le type de scan réalisé par nmap ?

Utiliser la commande time (voir "man time") pour chronometrer un connect scan à destination de gmail.google.com sur les 1024 premiers ports. Réaliser la meme opération concernant un SYN scan à destination de gmail.google.com. Conclusion ?


Lequel d'un connect scan ou d'un SYN scan vous semble le plus discret et le moins à même de laisser des traces dans les fichiers logs de gmail.google.com ? Pourquoi ?

### BONUS: Ajouter des couleurs au moyen des "ANSI escape codes" 

Modifier votre code pour afficher des couleurs différentes suivant que le port est ouvert ou fermé.

Voir https://en.wikipedia.org/wiki/ANSI_escape_code et https://stackoverflow.com/questions/4842424/list-of-ansi-color-escape-sequences


### Résultats

Envoyer votre scanner final scanner.c ainsi que les réponses aux questions de ce TP à mon email du CNAM : jonathan.brossard at lecnam.net


### J'ai fini plus tôt !

Good for you ! S'attacher à réaliser les wargames disponibles ici pour progresser: https://overthewire.org/wargames/


