# Plugin **TaHomaLocal**
<img src="/docs/img/TaHomaLocal-Image.png" alt="Image Logo plugin" style="height: 40%; width:40%;"/>
<div style="height: 40%; width:40%;">
![TaHomaLocal_image](https://github.com/Eridani78/TaHomaLocal-Doc/blob/main/docs/img/TaHomaLocal-Image.png)
  <div/>
## Presentation
Le plugin **TaHomaLocal** est destiné à permettre une interface entre Jeedom et une box Somfy TaHoma (ou box Somfy équivalente éligible) sur laquelle l'API locale Somfy a été activée.

Pour rappel, une API (Application Programming Interface) permet de « connecter » un logiciel ou un service à un autre logiciel ou service afin d'échanger des données et des fonctionnalités.

Une fois installé et proprement configuré, le plugin **TaHomaLocal** permet alors sur le réseau local sur lequel la box est connectée (réseau local LAN) l'envoi de commandes et la lecture de données des dispositifs couplés à la box et pilotés/commandés par cette dernière.
Les envois et réceptions de données ne sont alors plus transmis et reçus via Internet et via un serveur Somfy, les échanges restent internes au réseau local.

Il en résulte un fonctionnement 'cloudless' ou indépendance vis à vis d'Internet et pour les commandes compatibles, un retour d'état quasi instantané.

## Ecosystème Somfy/TaHoma
L'écosystème Somfy TaHoma comprend, à ce jour, de nombreux partenaires et est susceptible de continuer à s'étoffer et évoluer.
Cela signifie qu'une box TaHoma peut s'interfacer à de nombreux dispositifs très différents les uns des autres pour les piloter.
On trouve actuellement dans l'écosystems Somfy le controle de dispositifs tels que des systèmes de controle d'ouverture ou fermeture d'ouvrants (volets roulants, portes, stores, ...), des systèmes d'alarme, des systèmes de chauffage et climatisation, ...

L'absence de documentation de la part de Somfy sur les commandes des dispositifs rend la syntaxe de ces opérations particulièrement difficile à anticiper et implémenter dans un plugin et ce, à priori.

Afin de s'adapter au mieux à une telle diversité de commandes ou données potentielles, deux modes de fonctionnement du plugin ont du être implémenté.

Mode **Smart**

Ce premier mode crée les commandes principales à l'utilisation d'un équipement donné. Le choix des commandes créées est issu d'une base de données "Composants" qui s'enrichit au fur et à mesure du déploiement du plugin. Pour cela, le plugin **TaHomaLocal** intègre un dispositif d'apprentissage.
Ce dispositif doit permettre, dans la mesure du possible, une adaptation du plugin aux différents dispositifs rencontrés.
Cette adaptation n'est pas automatique et peut nécéssiter la transmission par l'utilisateur de données enregistrées lors de l'initialisation du plugin.
Lors de la phase d'initialisation du plugin, et si le cas se présente, un message indiquera à l'utilisateur qu'un nouveau dispositif non inclus dans la base de données a été détecté.
Il reviendra alors à l'utilisateur de transmettre via le lien prévu à cet effet, les fichiers de donnée concernant les dispositifs non encore connus du plugin pour que ces derniers soient pris en compte et intégrés dans la base de données composants du plugin.
Aucune donnée sensible personnelle autre que les descriptifs des composants n'est transmise via ce lien.

Mode **Full**

Ce second mode crée, sans filtre, l'ensemble des commandes disponibles pour un équipement donné.
C'est un mode qui devra être choisi avec précaution car il met à disposition de l'utilisateur des commandes opérationnelles mais aussi des commandes de type "Admin" et des commandes de type "Settings" dont certaines peuvent modifier des réglages réalisés lors de l'installation de l'équipement souvent via les applications propriétaires par exemple.
Les syntaxes des paramètres nécessaires à l'utilisation de certaines commandes peuvent ne pas être connues du plugin.

## Etapes d'initialisation et de mise en oeuvre du plugin **TaHomaLocal**

### Etape 1 - Activation de l'API locale
L'activation de l'API locale doit être réalisée pas l'utilisateur de la box TaHoma après connection à son compte client en choisissant d'activer le "mode Développeur".
Il n'est pas garanti que tous les modèles de box Somfy acceptent l'activation d'un "mode Développeur". Il revient donc à l'utilisateur de s'assurer que son modèle de box Somfy est compatible de ce mode particulier.
Il est à noter que les conditions générales et règles Somfy pour le "mode Développeur" s'appliquent également au plugin **TaHomaLocal**.

### Etape 2 - Configuration / Configuration du plugin
#### Identifiants
La configuration du plugin nécessite que l'utilisateur saisisse dans la page **Configuration du plugin** ses identifiants de connection à son compte Somfy (Email & Mot de Passe).

#### Socket Port
Le plugin utilise une valeur par défaut pour cette donnée et dans la majorité des cas, l'utilisateur n'aura pas à utiliser ce champ. 
Pour parer à l'éventualité d'un cas de collision avec le port utilisé par un autre plugin, ce champ pourra être utilisé pour changer le numéro de port utilisé par le plugin **TaHomaLocal**.

#### Mode plugin
Sélectionner le mode du plugin. "Le mode "Smart" est le mode du plugin par défaut. "Full" est un mode avancé (voir description ci-dessus).

#### Cron
Pour un fonctionnement correct du plugin, les crons "cron" et "cron 10" doivent être conservés 'activés'.
<img src="/docs/img/TaHomaLocal-Configuration_du_plugin-Fonctionnalites.png" alt="Image Configuration_du_plugin-Fonctionnalites" style="height: 50%; width:50%;"/>

### Etape 3 - Découverte passerelles / Découverte des Boxs compatibles sur le réseau
Au lancement de cette action, le plugin scrute le réseau à la recherche d'une ou plusieurs boxs Somfy (ou compatible) qui y seraient connectées.
Seule la ou les box Somfy ayant l'API locale activée seront reconnues.
Dans le cas ou plusieurs boxs sont reconnues, Le plugin **TaHomaLocal** permet à l'utilisateur de sélectionner la box qui sera déclarée **passerelle (active)** pour le plugin.


### Etape 4 - Authentification de l'API / Authentification - Obtention d'un Token
Afin d'utiliser l'API locale de la box, il est nécessiare d'authentifier les échanges avec celle-ci.
Cette sécurisation imposée par Somfy est réalisée en obtenant lors de la phase d'initialisation un Token d'authentification auprès du serveur Somfy.
Une fois obtenu, ce Token sauvegardé au niveau de la box et du plugin est conservé et utilisé pour authentifier les échanges sur le réseau local.
Le renouvellement ou l'obtention d'un nouveau Token pourra, dans certaines conditions, être rendu nécessaire, en cas de Reset de la box par exemple.

La demande de Token ne peut être réalisée qu'après qu'une box ait été sélectionnée **passerelle (active)**.
Même si un seul Token est nécessaire, l'API Somfy a prévu la possibilité d'en obtenir plusieurs.
Le plugin **TaHomaLocal** intègre une fonctionnalité permettant d'obtenir un ou plusieurs Token(s) et de selectionner le Token actif.

### Etape 5 - Import équipements / Import des équipements
Au lancement de cette action, le plugin importe les équipement déclarés dans la box et crée les commandes associées à chaque équipement.

### Etape 6 - Utilisation
La configuration du plugin est terminée. Les commandes disponibles peuvent alors être intégrées, le cas échéant renommées et utilisées au sein de Jeedom.

## Apps mobiles ou autres
Dans la mesure ou elles ne sont pas installées sous Jeedom, l'installation et l'utilisation du plugin **TaHomaLocal** n'a pas d'incidence et n'empêche pas l'utilisation des applications dédiées, fournies par Somfy ou par ses partenaires avec les dispositfs de l'écosystem (apps sur téléphone mobiles par exemple).

## Liste des équipements enregistrés dans la Base de Données
La liste des équipements reconnus par le plugin est tenue à jour dans le changelog du plugin.
Dans cette liste, les composants sont décrits selon leur classification générique Somfy et non par leur marque commerciale ou modèle.

## Routines
La gestion des routines n'est, jusqu'à présent, pas supportée par l'API locale Somfy.

## Arrêt du Daemon
Même si cette opération est déconseillée, l'utilisateur peut décider de stopper le Daemon (dans le panel Configuration du plugin).
Dans ce cas, le Daemon redémarrera automatiquement après un temps de resynchronization du plugin qui pourra atteindre 10 mn.
Pendant ce temps, certaines commandes peuvent ne plus être opérantes.

## Evolution de la politique Somfy
Le concepteur du plugin **TaHomaLocal** ne pourra, en aucun cas et d'aucune manière, être tenu responsable d'une évolution de la politique Somfy qui conduirait à une évolution significative de l'API rendant le plugin inopérant ou à la suppression de l'accès, par Somfy, à l'API locale telle qu'elle a été définie lors de la conception du plugin.
