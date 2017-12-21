Cette sortie correspond à une évolution majeure du logiciel.

L’équipe de Lodel.org a travaillé à la création de nouvelles fonctionnalités, à l’apport d’améliorations et à la correction de bugs de la précédente version.

Voici ci-dessous la liste des améliorations et des nouvelles fonctionnalités apportées au logiciel dans la version 0.9 RC1 :

Évolutions dans l’interface privée
----------------------------------

- Il est désormais possible de réaliser des « drag’n’drop » (cliquer-glisser-déposer) des entités (collections, numéros, articles…) pour facilement changer l’ordre des entités
- Mise en place de l’affichage des alias qui permet d’établir des liens entre les entités
- Déploiement des conteneurs dynamiquement grâce à la technologie AJAX sans rechargement de page
- Affichage du sitemap en version XML qui n’était pas visible auparavant dans l’interface privée
- Lors du rechargement d’un document les fac-similés/index sont désormais gardés
- Lors de la création d’utilisateurs, un mail est maintenant envoyé à l’utilisateur créé contenant le login, le mot de passe et l’url du site
- Une liste des utilisateurs connectés s’affiche une fois connecté
- Un système de messagerie interne permet d’envoyer des messages aux autres utilisateurs de la revue
- Traduction du site et de l’interface : ajout d’une fonctionnalité permettant de récupérer toutes les variables de traductions contenues dans les templates et d’ajouter les entrées correspondantes si elles n’existent pas
- Amélioration du système de mise en maintenance d’un ou plusieurs sites

Évolutions dans l’interface publique
------------------------------------

- Possibilité de réduire le desk (bandeau affichant les fonctionnalités de l’interface privée) côté site

Gestion du modèle éditorial (ME)
--------------------------------

- Possibilité d’ajout d’un masque de validation de champs (supporte les expressions régulières) (voir http://blog.lodel.org/47)
- Export/mise à jour du modèle éditorial en XML (encore en phase béta)

Corrections de bugs
-------------------

- L’interface pour IE 7 a été débuggée
- Correction d’une erreur d’affichage sur la page de traductions : les langues affichées ne correspondaient pas forcément à la langue des variables

Amélioration du comportement
----------------------------

- Il y a désormais un seul point d’entrée dans Lodel : la gestion des requêtes se fait uniquement par le controller et non plus par l’index.php
- La gestion des accès restreint peut maintenant se faire par IP
- Il est maintenant possible de construire des urls du type www.monsite.com/[id] ([id] correspond à l’id de l’entité à afficher)
- Le système de cache recompile désormais automatiquement le template si celui-ci a été modifié depuis la dernière compilation (uniquement côté site et lorsqu’on est en mode debug)
- Ajout des constantes ‘backoffice’ et ‘backoffice-lodeladmin’ indiquant respectivement que l’on se trouve côté interface du site ou côté lodeladmin.
- Ajout d’un paramètre ‘nocache’ indiquant à la classe générant les pages web de ne pas utiliser le cache (lecture et écriture)

Améliorations dans le noyau
---------------------------

- Passage des classes en PHP 5
- Ajout de l’autoload pour les classes internes
- Passage du context de variable globale à une classe statique, et centralisation des variables de configuration en lecture seule
- Ajout d’un système de plugin (encore en phase béta) (voir http://www.lodel.org/wiki/index.php/Plugins)
- Gestion des erreurs grandement améliorée : suppression des ‘die’ intempestifs et ajout d’un gestionnaire d’erreurs interne centralisé
- Compatibilité avec le niveau d’erreur PHP E_STRICT

Optimisations du code
---------------------

- Pour améliorer les performances générales de Lodel, le parser LodelScript a été modifié pour intégrer ADOdb ( ADOdb (voir http://phplens.com/lens/adodb/docs-adodb.htm) est une API orientée objet offrant un support d’abstraction de bases de données) afin de pouvoir utiliser les drivers de base de données MySQL ou MySQLi (voir http://blog.lodel.org/43)
- Refonte de la classe générant les pages (voir http://blog.lodel.org/43)
- Conversion presque totale de Lodel pour utiliser ADOdb (seul le script d’installation utilise les fonctions mysql_*)
- Mise en cache de certains résultats SQL (templates, variables de traductions)
- Intégration de l’API HTMLPurifier (voir http://htmlpurifier.org) et suppression de la classe InputFilter
- Mise à jour des APIs PclZip (voir http://www.phpconcept.net/pclzip/) et ADOdb

Développement du code (LodelScript)
-----------------------------------

- Ajout des filtres lexplode (appel de la fonction PHP explode) et lmath (fonction mathématiques basiques : addition, soustraction, division, multiplication)
- Ajout de la syntaxe [#VAR.STRING.#VAR2….] permettant de parcourir un tableau multidimensionnel
- Gestion des variables de types tableau
