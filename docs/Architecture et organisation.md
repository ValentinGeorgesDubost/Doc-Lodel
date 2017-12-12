Architecture technique
======================

ATTENTION : cette documentation décrit de manière très générale le fonctionnement d'une version antérieure de Lodel (0.8). De nombreux points sont à revoir pour profiter pleinement des bénéfices d’utilisation attendus des design pattern MVC et DAO (maniabilité et extensibilité du code, séparation des compétences). Cette page de doc est donc partiellement obsolète.

Vue d’ensemble
--------------

Lodel est structuré selon le modèle MVC (Modèle-Vue-Contrôleur), qui vise à séparer et rendre indépendantes les trois couches suivantes :

- modèle (ou couche métier, ou logique) : il est chargé d’effectuer les traitements et accès aux données ;
- vue (ou couche présentation) : il s’agit de l’interface utilisateur, qui est chargée d’afficher les résultats des traitements effectués par le modèle ;
- contrôleur : il est chargé d’intercepter les requêtes effectuées par le client, et d’appeler le modèle et la vue nécessaires pour traiter les requêtes.

Pour plus d’informations concernant l’architecture MVC, Cf. :

- une très brève explication : <http://fr.wikipedia.org/wiki/Mod%C3%A8le-Vue-Contr%C3%B4leur>
- une documentation détaillée sur une implémentation possible en PHP : <http://tahe.developpez.com/web/php/mvc/>

Dans Lodel, pour chaque requête effectuée par un client, les étapes suivantes sont exécutées :

- Le client envoie sa requête, qui est interceptée par le contrôleur.
- Le contrôleur appelle, si nécessaire, le modèle adéquat pour traiter la requête : le modèle effectue alors les traitements et accès aux données nécessaires.
- Le modèle renvoie le résultat de ses traitements au contrôleur.
- Le contrôleur appelle la vue adéquate, en lui passant la réponse reçue du modèle.
- La vue est envoyée au client.


Le contrôleur
-------------

Le contrôleur remplit successivement deux fonctions, qui sont définies dans des fichiers distincts :

- Initialisation de l’application : les fichiers index.php interceptent chaque requête, configurent l’application puis, en fonction de la requête, appellent soit le contrôleur principal, soit la vue. Ils constituent les seules portes d’entrée de l’application : ils jouent le rôle de « front controler ».
- Traitement de la requête : le fichier controler.php, se charge de l’appel du modèle et de la vue adéquate.

Les fichiers index.php
----------------------

Il y en a cinq, chacun d’entre eux correspondant à une porte d’entrée de l’application, i.e. à une interface et des traitements particuliers. Le tableau suivant donne la liste de ces fichiers.

Nom du fichier	                    Porte d’entrée
index.php                           accueil lodel (donne accès aux autres index.php)
lodeladmin/index.php                administration lodel
lodel/src/lodel/admin/index.php     administration d’un site
lodel/src/lodel/edition/index.php   édition
lodel/src/index.php                 consultation d’un site

Ces fichiers sont chargés d’intercepter les requêtes. La structure d’une requête peut être l’une des suivantes :

- http://hote/site/index.php?id=44 : pour l’affichage du contenu dont l’identifiant est 44 dans la base de données (typiquement utilisé dans l’interface publique) ;
–> À REVOIR : le fichier index.php à la racine d’un site
- http://hote/site/index.php?do=list&lo=class : pour effectuer l’action list sur la table class (et avec la classe métier class). Paramètres supplémentaires : classtype, id ;
- http://hote/site/index.php?page=dashboard : pour appeler un template particulier ;
- http://hote/site/backup.php : pour appeler un script particulier.
–> À REVOIR : les 2 derniers points

Pour chaque requête, un fichier index.php effectue successivement les opérations suivantes :

- Initialiser l’application (insertion des fichiers de configuration siteconfig.php et lodelconfig.php) : définition des chemins (de l’application en général et du site en particulier), de la base de données, informations de localisation (setlocale), etc.
- Assurer l’authentification de l’utilisateur et vérifier la session en cours (insertion du fichier auth.php), avec, au passage, initialisation de la connexion à la base de données (connect.php).
- Initialiser la variable globale $context, qui sert à stocker toutes les données utiles pour le fonctionnement de l’application (variables issues des fichiers de configuration, requête, jeu de caractères, utilisateur en cours, contenu à afficher, etc. –> À DOCUMENTER PLUS LOIN).
- Analyser les paramètres de la requête : en fonction de ces paramètres, il faudra appeler soit le fichier controler.php, soit la vue.
- Si des traitements doivent être effectués par le modèle, transmettre au fichier controler.php la requête et les logiques autorisées pour la traiter. C’est ce même fichier qui sera ensuite chargé d’appeler la vue.
- Sinon, appeler la vue adéquate.

Différence entre les étapes 5 et 6 (ou quand a-t-on besoin du modèle ?) :

- le modèle est appelé pour toutes les requêtes contenant les paramètres do (action à effectuer) et lo (classe métier avec laquelle effectuer l’action). En gros, le modèle est appelé pour effectuer des actions susceptibles de modifier les données dans la base (appel systématique dans la partie administration de l’interface privée).
- la vue est appelée pour les requêtes contenant les paramètres id (ou un identifiant littéral) ou page (pour l’appel d’une page statique). Elle est directement appelée lorsque que les accès à la base de données se font uniquement en lecture.

À MÉDITER POUR LA VERSION 0.9 : réunir tous ces fichiers dans un seul, pour éviter de recopier les mêmes lignes de code dans des fichiers différents, et centraliser le routage.

Le fichier controler.php
------------------------

La classe contrôleur (lodel/scripts/controler.php) est instanciée par l’un des fichiers index.php, qui lui transmet le nom de la classe métier qui doit effectuer les traitements nécessaires pour traiter la requête.
Elle se charge successivement de :

- Analyser la requête, la nettoyer pour prévenir certaines attaques et stocker ses paramètres dans $context.
- Instancier la classe du modèle (paramètre de la requête : lo) chargée d’effectuer les traitements : les méthodes de cette classe correspondent aux actions possibles (paramètre de la requête : do). Le nom de la classe correspond au nom de la table dans la base.
- Si l’action demandée lors de la requête correspond à une méthode définie dans la classe du modèle instanciée, le contrôleur demande le traitement de cette action.
- En fonction de la réponse du modèle, appeler la vue nécessaire pour afficher les résultats des traitements.

Le modèle
---------

Le modèle (ou logique) comprend :
- Les scripts chargés des traitements :
  - la classe mère (lodel/scripts/logic.php), qui définit la plupart des actions possibles (ajout, édition, suppression, copie, etc.).
  - les classes filles (lodel/scripts/class.xxx.php, où xxx est le nom d’une logique particulière), qui héritent des actions définies dans logic.php, les redéfinissent éventuellement, voire en ajoute.

- Les scripts chargés des accès à la base de données :
  - la couche d’abstraction DAO (la classe mère lodel/scripts/dao.php et les classes filles lodel/scripts/dao/class.xxx.php), qui est une première couche d’abstraction des données, et qui devrait être (n’est pas) le seul accès possible à la base –> À REVOIR
  - la surcouche adodb (lodel/scripts/adodb/adodb.inc.php), appelée par la couche DAO (ou directement appelée dans les scripts php), et qui se charge d’accéder à la base de données –> À REVOIR : utilité/besoin de cette sousousousousouscouche ?

Lorsque le contrôleur demande l’exécution d’une action, le modèle effectue successivement les opérations suivantes :

- La classe logic instanciée se charge d’instancier la classe DAO requise pour accéder aux données : une classe DAO fille correspond à une table dans la base. Elle contient la description en PHP de la table (liste des champs) et le niveau de droits requis pour effectuer des actions. La classe DAO mère définit les méthodes permettant de manipuler les données dans la base.
- La classe DAO instanciée utilise la couche adodb pour effectuer les opérations sur les données.
- La couche adodb renvoie ses résultats à la classe DAO, qui les transmet à la classe logic, qui les transmet au contrôleur.

La vue
------

La vue comprend :

- La classe lodel/scripts/view.php, qui est un singleton (une seule instanciation, accessible pour tous les autres objets).
- Le parser lodelscript : classes lodel/scripts/lodelparser.php et lodel/scripts/parser.php

La vue est appelée dans deux cas de figure :

- Par la classe contrôleur, si des traitements ont été effectués par le modèle.
- Par un fichier index.php, sinon.

Lorsque le contrôleur demande l’affichage d’une page, les opérations suivantes sont successivement effectuées :

- Le contrôleur crée une instance (ou récupère l’objet en cours) de la vue ($view = &View::getView).
- En fonction de la réponse du modèle suite à ses traitements, trois cas de figure se présentent :
  - en cas d’erreur, le message d’erreur est directement affiché à l’écran, une erreur 403 ou 404 est envoyé selon le type d’erreur ;
  - appel de la méthode back de la classe view : pour rediriger l’utilisateur vers une page précédemment consultée (en général, la dernière)
  - appel de la vue adéquate (cas le plus fréquent) : le contrôleur lui passe en arguments le contenu à afficher ($context), le nom du template (même nom que la classe logique instanciée, et donc même nom que la table dans la base), ainsi qu’un booléen qui indique s’il faut utiliser le cache ou non (le cache est utilisé seulement lorsqu’une requête contient l’action « list », il est désactivé pour toutes les autres actions).

- Si le cache est désactivé, la vue génère une nouvelle page en faisant appel au parseur lodelscript, puis l’affiche.
- Si le cache est activé (action=list), la vue affiche le contenu du cache, s’il est valide, demande le calcul d’une page sinon.

Dans le second cas de figure, lorsque la vue est appelée sans que le modèle ne l’ait été, le cache est systématiquement utilisé. On a donc les opérations suivantes :

- Instanciation de la vue.
- Affichage de la page cachée s’il y en a une version dans le cache.
- Sinon, génération d’une page, et affichage.
