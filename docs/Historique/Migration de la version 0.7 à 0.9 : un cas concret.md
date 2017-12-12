Dans le cadre d’un partenariat, nous avons eu pour mission de migrer un site de lodel 0.7 vers lodel 0.9, appelons le asgb. Nous avons reçu les données du site sous la forme d’un fichier compressé comprenant une sauvegarde des données réalisée dans l’interface lodel et l’arborescence du site. A cause de l’existence d’incompatibilités entre les versions récentes de php et la version 0.7 de lodel, nous réservons une machine aux projets de migration, appelons la oldserver, sous debian 5.0.10 sur laquelle est installée la version 5.2.1 de php et la version 5.0.51 de MySql, les bases étant créées par défaut en utf8. Le répertoire /www/lodel07 contient la racine de notre installation lodel 0.7 .


Création du site en lodel 0.7
-----------------------------

Dans un contexte réel, nous ne le redirons jamais assez, il est impératif de sauvegarder les données (base de données, fichiers annexes, maquettes, …). Le plus simple, en situation de production, nous semble être de recréer un site à l’identique en suivant notre procédure, à partir d’une sauvegarde de votre site.

Sur oldserver, nous créons un répertoire réservé aux fichiers produits pendant les différentes étapes de la migration, cela permet de minimiser les retours en arrière en cas de problème, soit /www/asgb. Nous y plaçons la sauvegarde de la base de données faite sous lodel, fichier asgb.sql . Ce fichier est encodé en utf8 (commande file asgb.sql). Un affichage du contenu de ce fichier montre que les tables lodel étaient préfixées par lodel_ , ce qui est incompatible avec notre installation.


        CREATE TABLE IF NOT EXISTS `lodel_champs` (
            `id` int(10) unsigned NOT NULL AUTO_INCREMENT,
            `nom` varchar(64) NOT NULL DEFAULT '',
            `idgroupe` int(10) unsigned NOT NULL DEFAULT '0',
            
Nous devons donc éditer ce fichier pour supprimer ce préfixe lodel_, le résultat est enregistré dans  asgb2.sql .

Le site ASGB est créé dans l’interface lodel 0.7 avec le nom court asgb, les fichiers lodel sont copiés dans /www/lodel07/asgb .
Dans notre installation, les bases sont préfixées par le préfixe lodel07_ . La base de données a donc pour nom lodel07_asgb. Elle a été créée en utf8 selon la configuration de notre serveur. Si votre serveur et vos bases sont configurés en latin1, il est inutile de faire le traitement spécial indiqué ci-dessous ; vous pouvez importer vos données (mysql  lodel07_asgb <  /www/asgb/asgb2.sql) et passer à  l’étape « Export 0.7 vers 0.8 ».

Traitement spécial latin1 -> utf8
---------------------------------

Le fichier /www/asgb/asgb2.sql est un fichier utf8 contenant des données encodées en latin1. Il faut que la base lodel07_asgb qui contiendra les données importées soit également en latin1. Avant d’importer les données, il faut donc détruire la base créée en utf8 et créer une base latin1

    DROP  database  lodel07_asgb ;
      CREATE  DATABASE  lodel07_asgb  DEFAULT  CHARACTER  SET  'latin1'  COLLATE  latin1_general_ci;

Les données sont ensuite importées dans cette nouvelle base :

    mysql  --default-character-set=latin1  lodel07_asgb  <  /www/asgb/asgb2.sql

Le charset est modifié et les données sauvegardées dans le fichier /www/asgb/asgb3.sql :

    mysqldump  lodel07_asgb --default-character-set=latin1  |  sed  s/CHARSET=latin1/CHARSET=utf8/g | sed  s/'SET NAMES latin1'/'SET NAMES utf8'/g  >  /www/asgb/asgb3.sql

Visualisez rapidement le fichier  /www/asgb/asgb3.sql pour vérifier que l’encodage est correct.

Une dernière étape consiste à modifier l’encodage du charset de la base pour le passer en utf8 :

    ALTER  DATABASE  `lodel07_asgb`  DEFAULT  CHARACTER  SET  'utf8'  COLLATE  utf8_general_ci ;

Il ne reste qu’à importer les données utf8 dans la base utf8 et à sauvegarder :

    mysql  --default-character-set=utf8  lodel07_asgb  <  /www/asgb/asgb3.sql
     mysqldump  lodel07_asgb  >  /www/asgb/asgb4.sql

Export 0.7 vers 0.8
-------------------

A cette étape, le site est créé en lodel 0.7, l’encodage est en utf8, les données sont sauvegardées dans /www/asgb/asgb4.sql s’il y a eu une transformation latin1-utf8 ou bien dans /www/asgb/asgb2.sql sinon. Un parcours depuis l’interface lodel permet de vérifier que les documents sont valides mais le site est inaccessible car il manque en général des templates (dans notre cas http://oldserver.revues.org/lodel07/asgb/lodel/admin/index.php).

Les fichiers suivants sont nécessaires à l’exportation :

- export_to_08.php  à la racine du site à exporter /www/lodel07/asgb
- 07to08.php  dans lodel/scripts de l’installation multisite de Lodel soit /www/lodel07
- index_migration.html  dans le répertoire tpl du site /www/lodel07/asgb/tpl
- macros_technique.html  dans le répertoire tpl du site /www/lodel07/asgb/tpl
- Il faut que répertoire tpl soit accessible en lecture pour l’utilisateur apache
- init-site.sql  à la racine du site /www/lodel07/asgb

Vérifiez que les fichiers du répertoire tpl sont accessibles à l’utilisateur apache et connectez-vous dans l’interface d’administration du site pour lancer le script d’export export_to_08.php (dans notre cas http://oldserver.revues.org/lodel07/asgb/export_to_08.php). Décochez la case Sauvegarde et cliquez sur Valider. Si l’export a été fait avec succès, il faut maintenant supprimer les entités dont le statut d’import est « non terminé ».

    mysql lodel07_asgb
     > delete from documents  where identity in (select id from entities e where e.status=-64);
     > delete  from  relations  where  id2  in  (select id from entities e where e.status=-64);
     > delete  from  entities  where  status=-64;

Une sauvegarde est nécessaire à cette étape avant l’importation sous lodel 0.9 :

    mysqldump  lodel07_asgb  >  /www/asgb/asgb5.sql
 

Migration sous lodel 0.9
------------------------

Création du site et importation des données
-------------------------------------------

Notre serveur de développement develserver.revues.org contient une installation de lodel 0.9 multisites dans le répertoire /www/lodel09 . Les noms des bases sont préfixés avec le préfixe lodel09_ . Nous créons maintenant un site lodel ASGB sur cet espace, son répertoire racine sera /www/lodel09/asgb . La base correspondante est lodel09_asgb en utf8. Il faut ensuite détruire puis recréer la base avant d’importer les données exportées de 0.8 :

    mysql
     > drop  database  lodel09_asgb ;
     > create database  lodel09_asgb ;
     > quit ;
     mysql  lodel09_asgb  <  /www/asgb/asgb5.sql

Quelques commandes doivent être effectuées pour être compatibles avec la version 0.9 :

    mysql  lodel09_asgb
     > alter  table  tablefields  add  mask  text  not  null;
     > alter  table  entrytypes  add  `externalallowed`  tinyint(4)  NOT  NULL  default  '0' ;
     > CREATE TABLE `plugins` (
       `id` int(10) unsigned NOT NULL DEFAULT '0',
       `name` varchar(64) CHARACTER SET utf8 COLLATE utf8_bin NOT NULL,
       `upd` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
       `status` tinyint(4) NOT NULL DEFAULT '0',
       `config` longtext NOT NULL,
       PRIMARY KEY (`id`),
       UNIQUE KEY `name` (`name`)
     ) ENGINE=MyISAM DEFAULT CHARSET=utf8 ;
     > CREATE TABLE `relations_ext` (
       `idrelation` int(10) unsigned NOT NULL AUTO_INCREMENT,
       `id1` int(10) unsigned NOT NULL DEFAULT '0',
       `id2` int(10) unsigned NOT NULL DEFAULT '0',
       `nature` varchar(32) NOT NULL DEFAULT 'E',
       `degree` tinyint(4) DEFAULT NULL,
       `site` varchar(64) NOT NULL,
       PRIMARY KEY (`idrelation`),
       UNIQUE KEY `id1` (`id1`,`id2`,`degree`,`nature`),
       KEY `index_id1` (`id1`),
       KEY `index_id2` (`id2`),
       KEY `index_nature` (`nature`),
       KEY `index_site` (`site`)
     ) ENGINE=MyISAM DEFAULT CHARSET=utf8 ;
    > CREATE TABLE `history` (
      `id` int(10) unsigned NOT NULL AUTO_INCREMENT,
      `nature` varchar(32) NOT NULL,
      `context` text,
      `upd` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
      PRIMARY KEY (`id`)
      ) ;

Il est très très important de sauvegarder les données avant l’étape délicate de l’importation du modèle éditorial au format XML.

A ce stade, nous disposons d’un site Lodel fonctionnel sous Lodel 0.9. Le modèle éditorial utilisé dans ce site est celui qui a été défini dans le site sous Lodel 0.7.

Importation du modèle éditorial
-------------------------------

Nous souhaitons maintenant mettre à jour le modèle éditorial de notre site pour qu’il soit conforme au modèle éditorial actuellement utilisé dans Lodel 0.9. Nous allons utiliser une fonctionnalité définie dans Lodel 0.9 qui nous permet d’importer un modèle éditorial (que nous appellerons cible) dans un site contenant déjà un modèle éditorial (que nous appellerons source). Au cours des différentes étapes de l’import, nous allons devoir faire correspondre l’ensemble des éléments qui diffèrent entre les modèles source et cible.

Dans l’interface Lodel 0.9, accédez au site migré et sélectionnez le menu Administration / Modèle éditorial / Importer un modèle au format XML . Nous utilisons le fichier modelxml-migration-260109.zip (téléchargement modelxml-migration-260109). Le système va vous proposer une succession de correspondances entre les champs de l’ancien site et les champs sous Lodel 0.9 . Il s’agit de reporter tous les chiffres du premier tableau dans le deuxième tableau en respectant le champ et la classe. Il ne faut pas utiliser la touche Entrée pour valider vos choix, mais cliquer sur le bouton Envoyer.

- la table documents devient la table textes
- pour la table tablefieldgroups, la correspondance est évidente

![Screenshot1](image/migration-lodel-1.png)

- table options
   - servoourl devient url, servoousername devient username, servoopass devient passwd
   - signaler_mail n’existe pas en 09
- tables orphelines : la table documents devient textes
- classe publications :
   - erratum : champ vide et groupe des addenda
- classe textes
  - notesbaspage devient notebaspage dans le groupe Texte
  - historique, fichiersassocies, fichiersource, importversion dans Gestion du document
  - droitsauteur vide et dans le groupe Metadonnées
  - lien dans le groupe Texte
  - URLessai dans Titres

![Screenshot1](image/migration-lodel-2.png)

- classe types
  - regroupement = sous-partie
  - presentation = informations
  - articlepdf = article
  - regroupement-documentsannexes = vide
  - documentannexe-lienfichier = fichierannexe
  - documentannexe-lienfacsimile = fichierannexe
  - documentannexe-liendocument, documentannexe-lienpublication, documentannexe-lienexterne = lienannexe
  - articlevide = article
  - objetdelarecension = vide
  - recension = compterendu
  - volume, colloque = rubrique
  - breve = billet
  - periode = chrono
  - motcle = motsclesfr
  - textes devient textessimples (lien=url, datepubli=date)
  - correspondance des types

![Screenshot1](image/migration-lodel-3.png)

- correspondance types textes vers liens

![Screenshot1](image/migration-lodel-4.png)


Finitions
---------

- sauvegarder la base (fichier asgb7.sql)
- rendre les documents cliquables : update  textes  set  documentcliquable=1;
- copier le fichier complete.php à la racine du site migré, l’éditer pour supprimer la ligne « exit(); » au début du fichier et terminer la migration en lançant le script dans l’interface lodel (http://develserver.revues.org/lodel09/asgb/complete.php)
- effacer le fichier complete.php
- copier les documents annexes fournis avec l’ancien site ainsi que les fichiers sources ; rendre les répertoires docannexe et lodel/sources accessibles en écriture à l’utilisateur apache.
