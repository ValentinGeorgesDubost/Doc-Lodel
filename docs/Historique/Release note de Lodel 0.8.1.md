Lodel 0.8.1 : première mise à jour de Lodel 0.8
-----------------------------------------------

Après la sortie en octobre 2007 d’une version majeure de Lodel, la version 0.8, voici aujourd’hui celle d’une première mise à jour, la Lodel 0.8.1.

L’équipe de Lodel.org a travaillé à la création de nouvelles fonctionnalités, à l’apport d’améliorations et à la correction des premiers bugs constatés.

Les nouveautés de Lodel 0.8.1
-----------------------------

Attention : tous les développements sont optimisés pour fonctionner en PHP5. Cette version de Lodel n’est plus compatible avec PHP4.

Nouvelles fonctionnalités, améliorations et mises à jour :
----------------------------------------------------------

- possibilité pour un admnistrateur Lodel de forcer un utilisateur à modifier son mot de passe
- ajout du filtre preg_replace : possibilité de chercher/remplacer les occurences d’une expression régulière
- amélioration de l’utilisation des champs multilingues dans le Lodelscript : ajout de la variable globale ‘defaultlang’ contenant toutes les langues disponibles par défaut
- possibilité de choisir le répertoire d’extraction des fichiers importés par le Servoo : ajout de la variable globale $tmpoutdir
- mise à jour de Wikirenderer

Corrections de bugs :
---------------------

- le comportement de FCKEditor (barre d’outils de mise en forme) a été optimisé
- l’export de données est à nouveau disponible

Une description complète de ces corrections est accessible sur Sourcesup, la plate-forme web de gestion de projet destinée aux établissements d’enseignement supérieur : http://sourcesup.cru.fr/tracker/?group_id=193

Pour effectuer la mise à jour de Lodel 0.8 vers Lodel 0.8.1, 2 possibilités vous sont offertes:

Mises à jour
------------

Mise à jour manuelle des fichiers :
-----------------------------------

- faire une copie de sauvegarde du répertoire d’installation de Lodel : cp -pR monLodel monLodel.old
- décompresser l’archive (tar.gz ou .zip) dans un répertoire temporaire : tar xvzf lodel-0.8.1.tar.gz
- copier tous les fichiers de la nouvelle version dans votre répertoire d’installation de Lodel : cp -pR lodel/* monLodel/
Les fichiers sont disponibles à cette adresse : http://sourcesup.cru.fr/frs/?group_id=193

Mise à jour avec Subversion :
-----------------------------

Les versions 0.8.x sont sur la branche version_0_8-bugfixes-branch. Si vous avez installé Lodel 0.8.x avec Subversion, vous avez donc effectué le checkout suivant : svn checkout http://subversion.cru.fr/lodel/branches/version_0_8-bugfixes-branch monLodel

Pour mettre à jour votre version, il suffit de faire un update, en exécutant les commandes suivantes :

- cd monLodel
- svn update
