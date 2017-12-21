Nous annonçons enfin la publication de Lodel 1.0 qui était en préparation à OpenEdition depuis plus de 2 ans !

Le changement majeur de Lodel 1.0 est l’utilisation du format XML TEI <http://www.tei-c.org> à la place du XML « R2R » non standard utilisé jusque-là. Ce changement de format XML va de paire avec le remplacement de l’application de conversion ServOO par OTX. Comme ServOO, OTX convertit des documents de traitement de texte stylés, mais le format de sortie est TEI. Ce passage à un standard XML permet l’import direct de XML dans Lodel, ce qui ouvre la porte à une utilisation du logiciel dans un environnement d’édition basé sur le Single Source Publishing.

Vous trouverez plus de détails sur les nouveautés dans les paragraphes suivants.


Lodel 1.0
---------

Passage à GitHub
----------------

A l’occasion de la publication de Lodel 1.0, nous avons choisi de rejoindre GitHub pour la publication de Lodel. Nous pensons que cette plateforme, devenue incontournable, permettra un élargissement de la communauté des utilisateurs et contributeurs de Lodel.

La branche « master » du dépôt svn de sourcesup est synchronisée avec la branche « master » du dépôt GitHub et restera donc à jour. Les prochaines releases seront par contre disponibles uniquement sur GitHub.

Lodel 1.0 est donc disponible à l’adresse suivante : https://github.com/OpenEdition/lodel

La dernière version de Lodel est la version 1.0.1 que vous pouvez obtenir sur GitHub à cette adresse : https://github.com/OpenEdition/lodel/tree/v1.0.1 ou dans les pages GitHub du projet Lodel : http://openedition.github.io/lodel/ en téléchargement.

Nouveautés de Lodel 1.0
-----------------------

- utilisation du format XML TEI comme format XML d’import au lieu de format XML R2R utilisé jusque là. Le logiciel de conversion qui remplace ServOO est OTX. Il produit donc des fichiers XML TEI compatibles avec Lodel. Il est également possible d’importer directement des documents au format XML.
- réécriture de la gestion du cache.
- ajout d’un système de hook qui permet d’exécuter une fonction à la validation d’un formulaire d’édition.
- index mutualisés : permet de partager un index d’un site Lodel avec les autres sites de la même installation de Lodel.
qualification des relations entre entité et entrée d’index sur le modèle de ce qui existait précédemment entre entité et index de personnes.
- sécurité d’édition concurrente : évite les pertes de données en cas d’édition d’un objet depuis plusieurs endroits simultanément.
- nouveaux types de champs : MLdate, MLlongtext
- réécriture de certains filtres
- ajout d’un mode debug pour afficher le code php résultat du parsing Lodelscript (paramètre showphp=true passé en get dans l’url)
- ajout de fonctions de manipulation du modèle éditorial (dans lodel/install/scripts) : permet de scripter des modifications de modèle éditorial
- ajout d’un script de nettoyage des sources non liées à une entité (dans lodel/install/scripts).
- réécriture de la fonction de détection de la langue
- abandon de pclzip et unzip au profit de ziparchive
- abandon de MagPie RSS au profit de SimplePie
- compatibilité php 5.3 et 5.4

Procédure de mise à jour de Lodel 0.9 à Lodel 1.0
-------------------------------------------------

Pour la mise à jour de 0.9 en 1.0, après avoir mis à jour le code de Lodel copier le fichier lodel/install/upgrade/1.0.0.php à la racine du site et accéder à ce fichier par le navigateur : http://mondomaine.com/monsite/1.0.0.php, suivre les instructions et vérifier que les requêtes ne sont pas erronées, puis valider l’exécution des requêtes en bas de page.

Une fois cette étape réalisée, il faut supprimer le fichier 1.0.0.php de la racine du site. Une fois cette étape faite pour chaque site, se rendre à la racine de l’installation de lodel, et exécuter tous les scripts présents dans le répertoire lodel/install/upgrade/ dans l’ordre sauf 1.0.0.php :
monserver:/var/www/lodel# php lodel/install/upgrade/1.0.1.php
monserver:/var/www/lodel# php lodel/install/upgrade/1.0.2.php
Lors de prochaines mises à jour, les scripts 1.0.* seront à exécuter de la même manière.

TEI OpenEdition
---------------

Le modèle éditorial publié avec Lodel 1.0 (me-revorg) est compatible avec le schéma TEI OpenEdition.

La documentation sur le format TEI est disponible sur le site de Lodel : http://www.lodel.org/701.

Le schéma XML W3C pour l’encodage TEI Openedition est disponible à l’adresse http://www.lodel.org/ns/. La documentation technique du schéma est consultable à l’adresse http://www.lodel.org/715.

Dans le cas d’une utilisation de Lodel avec import de documents stylés via OTX, les utilisateurs n’ont pas besoin d’aborder ces questions d’XML. OTX assure la conversion et l’interface avec Lodel.

OTX et Service de conversion
----------------------------

OTX
---

OTX est le logiciel de conversion doc/odt vers XML TEI utilisé par Lodel pour importer des documents de traitement de texte stylés. Il est diffusé sous licence GPL2, comme Lodel.

Il est disponible sur GitHub à l’adresse suivante : https://github.com/OpenEdition/OTX

La version actuelle est la version 1.0.1 : https://github.com/OpenEdition/OTX/tree/v1.0.1

L’installation est assez simple et bien documentée.

Une fois l’installation terminée, le script install/create_user.php permet la création d’un utilisateur OTX qu’il faut ensuite reporter dans la section OTX du fichier de configuration de Lodel lodelconfig.php

Limite connue

Le projet d’écriture de l’application OTX prévoyait une totale adaptabilité d’OTX au modèle éditorial de Lodel. En spécifiant des informations sous forme de XPath dans le modèle éditorial du site Lodel, OTX devrait être capable de convertir le document de traitement de texte stylé en XML TEI sur la base de ce XPath.

Concrètement, OTX n’est que partiellement dynamique. Certaines spécifications de XPath dans le modèle éditorial de Lodel sont prises en compte par OTX, d’autres non. La liste des cas non-reconnus n’est pas documentée. Nous avons choisi de publier Lodel 1.0 et OTX 1.0 malgré cette limite.

Nous prévoyons des améliorations mais sans calendrier pour le moment. OTX étant un logiciel libre, toute contribution est bienvenue.

Service de conversion
---------------------

Parallèlement à la publication du code d’OTX, nous allons prochainement proposer le service web qui permettra de convertir vos fichiers de traitement de texte stylés. Ce service évite l’installation et la maintenance d’OTX sur votre serveur. Il pourra utiliser plusieurs serveurs de conversion en fonction des besoins pour une meilleure disponibilité.

Il sera gratuit pour un usage limité (publication d’une seule revue) et sera payant pour une utilisation plus importante. Cette contribution nous aidera à améliorer le logiciel et la fiabilité du service.
