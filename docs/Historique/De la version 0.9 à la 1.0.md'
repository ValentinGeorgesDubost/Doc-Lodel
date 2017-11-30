L’installation multi-sites de Lodel 0.9 se trouve dans le répertoire /www/09 . Nous disposons également d’une installation multi-sites de Lodel 1.0 dans le répertoire /www/10 . Le nom des bases de données associées à cette version est préfixé par lodel10_ .
Il s’agit de migrer le site ASGB de la version 0.9 à la version 1.0 : le répertoire associé est /www/09/asgb, lodel09_asgb est la base de données associée.

Nous utilisons un espace de développement dont la structure est identique à celle de l’espace de production. Ceci nous semble indispensable, surtout si le nom des bases de données n’est pas préfixé par une chaîne de caractères liée au numéro de version.


Création du site sous Lodel 1.0
Elle commence par le blocage du site en production depuis l’interface Lodel 0.9. Puis nous vous conseillons de sauvegarder la base de données : mysqldump  lodel09_asgb  >  /data/tmp/lodel09_asgb.sql

Il faut ensuite sauvegarder les données 0.9 dans l’interface Lodel 0.9 et les copier sur l’espace de développement en 1.0 .

Le site est créé sur l’espace de développement : les fichiers sont situés dans /www/10/asgb et la base de données est lodel10_asgb . Une sauvegarde est souhaitable à ce niveau : mysqldump  lodel10_asgb  >  /data/tmp/asgb1.sql

Si le site a été migré depuis une version 0.7, il faut vérifier que les fichiers contenus dans le répertoire docannexe du site en production ont bien été copiés avec les données, en particulier le répertoire fichier.

Migration
Nous disposons donc sur l’espace développement de données en Lodel 0.9 sur une installation en Lodel 1.0.

Il faut copier le script de migration 1.0.0.php livré avec Lodel 1.0 (dans le répertoire lodel/scripts) dans le répertoire d’installation du site : cp  /www/10/lodel/install/upgrade/1.0.0.php   /www/10/asgb
L’exécution se fait dans le navigateur (en mode authentifié) : http://develserver.revues.org/10/asgb/1.0.0.php . A cette étape, le script affiche les commandes qu’il va lancer mais ne les exécute pas ; après vérification des requêtes proposées, il faut rechercher en bas de page le lien cliquable pour lancer l’exécution des requêtes.
Supprimer le fichier /www/10/asgb/1.0.0.php

Les données sont sauvegardées : mysqldump  lodel10_asgb  >  /data/tmp/asgb2.sql

Il reste à lancer les autres scripts 1.*.php  dans /www/10/lodel/install/upgrade en se plaçant dans le répertoire d’installation multi-sites dans notre cas /www/10 : php  lodel/install/upgrade/1.0.1.php puis php  lodel/install/upgrade/1.0.2.php
