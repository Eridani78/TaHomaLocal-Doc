# Plugin **TaHomaLocal**
<img src="/docs/assets/images/TaHomaLocal-Image.png" alt="" style="height: 20%; width:20%;"/>
<img src="/TaHomaLocal-Doc/assets/images/TaHomaLocal-Image.png" alt="TaHomaLocal logo" style="height: 20%; width:20%;"/>

## Presentation
Le plugin **TaHomaLocal** est destiné à permettre une interface entre Jeedom et une box Somfy TaHoma (ou box Somfy équivalente éligible) sur laquelle l'API locale Somfy a été activée.

Pour rappel, une API (Application Programming Interface) permet de « connecter » un logiciel ou un service à un autre logiciel ou service afin d'échanger des données et des fonctionnalités.

Une fois installé et proprement configuré, le plugin **TaHomaLocal** permet alors sur le réseau local sur lequel la box est connectée (réseau local LAN) l'envoi de commandes et la lecture de données des dispositifs couplés à la box et pilotés/commandés par cette dernière.
Les envois et réceptions de données ne sont alors plus transmis et reçus via Internet et via un serveur Somfy, les échanges restent internes au réseau local.

Il en résulte un fonctionnement 'cloudless' ou indépendance vis à vis d'Internet et pour les commandes compatibles, un retour d'état quasi instantané.

## Ecosystème Somfy/TaHoma
L'écosystème Somfy TaHoma comprend, à ce jour, de nombreux partenaires et est susceptible de continuer à s'étoffer et évoluer.
Cela signifie qu'une box TaHoma peut s'interfacer à de nombreux dispositifs très différents les uns des autres pour les piloter.
On trouve actuellement dans l'écosystèmes Somfy le contrôle de dispositifs tels que des systèmes de controle d'ouverture ou fermeture d'ouvrants (volets roulants, portes, stores, ...), des systèmes d'alarme, des systèmes de chauffage et climatisation, ...

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

Après activation du "mode Développeur" , il est conseillé d'effectuer une RESYNCHRONISATION de sa box Somfy pour que l'API Locale soit bien activée au niveau de la box.
Les modalités d'une resynchronisation d'une box Somfy sont très bien décrites sur internet.

### Etape 2 - Installation du plugin
Une fois le plugin installé, réaliser les opérations suivantes :
	- Dans **Etat** : Activer
	- Dans **Dépendances** : Relancer

#### Logs et surveillance
Le niveau log doit être conservé sur **Defaut**.
Les niveaux **Info ou Debug** peuvent être utilisés pour tracer d'éventuels problèmes mais d'une façon temporaire.


### Etape 3 - Configuration / Configuration du plugin
#### Modèle de box
Sélectionnez le modèle de votre box Somfy.

#### Identifiants
La configuration du plugin nécessite que l'utilisateur saisisse dans la page **Configuration du plugin** ses identifiants de connection à son compte Somfy (Email & Mot de Passe).

#### Mode plugin
Sélectionner le mode du plugin. "Le mode "Smart" est le mode du plugin par défaut. "Full" est un mode avancé (voir description ci-dessus).

#### Mode IP (optionnel)
En fonctionnement standard, le plugin réalise automatiquement la découverte de la box et de ses paramètres.
Les accès réseau à la box sont alors réalisés en utilisant son "hostname.local".
Dans certains cas (problèmes de résolution DNS par exemple) ou certaines configurations réseau, il peut être nécessaire d'utiliser l'adresse IP de la box en remplacement du hostname.

Dans ce cas, cocher la case Mode IP et compléter les champs requis.
Une fois saisis, les champs spécifiques au Mode IP peuvent être conservés mais ne seront pas utilisés si la case Mode IP n'est pas cochée.

#### Socket Port (optionnel)
Ce champ est a conserver **vide**.
Le plugin utilise une valeur par défaut pour cette donnée et dans la majorité des cas, l'utilisateur n'aura pas à saisir de valeur dans ce champ. 
Pour parer à l'éventualité d'un cas de collision avec le port utilisé par un autre plugin, ce champ pourra être utilisé pour changer le numéro de port utilisé par le plugin **TaHomaLocal**.




### Etape 4 - Découverte passerelles / Découverte des Boxs compatibles sur le réseau
Au lancement de cette action, le plugin scrute le réseau à la recherche d'une ou plusieurs boxs Somfy (ou compatible) qui y seraient connectées.
La ou les boxs Somfy ayant l'API locale activée sont identifiées dans le tableau.
Dans le cas ou plusieurs boxs sont reconnues, Le plugin **TaHomaLocal** permet à l'utilisateur de sélectionner la box qui sera déclarée **passerelle (active)** pour le plugin.
**Sélectionner** la passerelle active en cliquant sur le point puis quitter avec **Sauvegarder**.

### Etape 5 - Authentification de l'API / Authentification - Obtention d'un Token
⚠ Cette étape nécessite une connection à Internet.

Afin d'utiliser l'API locale de la box, il est nécessaire d'authentifier les échanges avec celle-ci.
Cette sécurisation imposée par Somfy est réalisée en obtenant lors de la phase d'initialisation un Token d'authentification auprès du serveur Somfy.
Une fois obtenu, ce Token sauvegardé au niveau de la box et du plugin est conservé et utilisé pour authentifier les échanges sur le réseau local.
Le renouvellement ou l'obtention d'un nouveau Token pourra, dans certaines conditions, être rendu nécessaire, en cas de Reset de la box par exemple.

La demande de Token ne peut être réalisée qu'après qu'une box ait été sélectionnée **passerelle (active)**.
Même si un seul Token est nécessaire, l'API Somfy a prévu la possibilité d'en obtenir plusieurs (Gestion multi-Jeedom par exemple).
Le plugin **TaHomaLocal** intègre une fonctionnalité permettant d'obtenir un ou plusieurs Token(s) et de selectionner le Token actif.
Le champs "Token Label" est optionnel et peut être laissé vide. Sinon, un texte peut être saisi pour personnaliser le nom du Token.
Le champ "Token Scope" est inopérant à l'heure actuelle.

### Etape 6 - Import équipements / Import des équipements
Au lancement de cette action, le plugin importe les équipement déclarés dans la box et crée les commandes associées à chaque équipement.

Si des équipements sont listés dans le tableau sous **Composants inconnus découverts**, cela signifie que ces nouveaux équipements ne sont pas encore intégrés dans la Base de Données (BDD) du plugin.
Prière de réaliser alors l'opération suivante :

1. En utilisant l'Editeur de Fichiers de Jeedom, se rendre dans le répertoire
> ```
> html/plugins/TaHomaLocal/data/components/undefined
> ```
Les équipements nouveaux se trouvent dans ce répertoire.

2. Sélectionner le réperoire `undefined`, puis clic droit souris **Créer une archive ZIP**, renommer l'archive obtenue en rajoutant `.txt` à la suite.

3. Fonction **Envoyer les fichiers** (flèche vers le haut du menu de la page) sur votre ordinateur.

4. Envoyer le fichier au concepteur du plugin (** important** en MP pour des aspects de confidentialité).

Les équipements seront intégrés à la BDD du plugin dans les meilleurs délais. 

#### Etape 7 - Démon
Il est inutile (mais possible) de démarrer le Démon manuellement.
Celui-ci démarrera de lui même lorsque toutes les conditions auront étét satisfaites.
Le plugin sera alors opérationnel au bout de 1 à 2 minutes.
Pendant cette phase de synchronisation du Démon, certains messages d'erreur pourront apparaitre et peuvent être ignorés.

### Etape 8 - Utilisation
La configuration du plugin est terminée.
Les commandes disponibles peuvent alors être intégrées, le cas échéant renommées et utilisées au sein de Jeedom.

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
L'entité Jeedom ainsi que le concepteur du plugin **TaHomaLocal** ne pourront, en aucun cas et d'aucune manière, être tenus responsables d'une évolution de la politique Somfy qui conduirait à :
- une évolution significative de l'API rendant le plugin inopérant, ou
- à la suppression de l'accès, par Somfy, à l'API locale telle qu'elle a été définie lors de la conception du plugin.
