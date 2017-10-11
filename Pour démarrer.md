1. Installation
---------------

Notez qu'une version pré-installée de Lodel (et OTX, l’application de conversion Word/Office vers XML/TEI) en tant qu’image de machine virtuelle linux Debian est téléchargeable à l’adresse : <http://lodel.org/downloads/vms/2017/>

Pré-requis:

Serveur HTTP (nginx, apache) avec PHP
Serveur MySQL/MariaDb
pour être utilisé avec OTX, il faut une valeur de max_allowed_packet et key_buffer très grande (16 M)
Marche à suivre:

Cloner de préférence la dernière version tagguée
Faire pointer le virtual host sur la racine de l'installation lodel.
L'utilisateur du serveur HTTP doit avoir les droits de lecture sur tous les fichiers.
Créer une base de donnée et un utilisateur ayant les droits de modification sur cette base.
Aller à l'adresse configurée avec un navigateur web, suivre les instructions.
Il faudra donner temporairement les droits d'écriture sur le dossier d'une instance de site.
Vérifer qu'à l'intérieur du dossier d'un site l'utilisateur du serveur HTTP a bien les droits d'écriture sur les dossiers: upload, docannexe, docannexe/file, docannexe/image, lodel/sources, lodel/icons


2. OTX (<https://github.com/OpenEdition/OTX>)
---------------------------------------------

OTX est l'application qui permet la conversion de fichiers de traitement de texte stylés en fichiers XML-TEI compatibles avec le modèle éditorial "Revues.org" distribué dans Lodel. Le projet d'écriture de l'application OTX prévoyait au départ une totale adaptabilité d'OTX au modèle éditorial de Lodel. En spécifiant des informations sous forme de XPath dans le modèle éditorial du site Lodel, OTX devait être capable de convertir le document de traitement de texte stylé en XML TEI sur la base de ce XPath. Concrètement, OTX n'est que partiellement dynamique. Certaines spécifications de XPath dans le modèle éditorial de Lodel sont prises en compte par OTX, d'autres non. La liste des cas non-reconnus n'est pas documentée. Nous avons choisi de publier Lodel 1.0 et OTX 1.0 malgré cette limite.

Le Cléo ne propose pas de service de conversion ouvert comme c'était le cas avec ServOO (le prédécesseur d'OTX, logiciel de conversion utilisé avec Lodel 0.8/0.9). Pour importer des documents de traitement de texte, il faut donc installer aussi OTX.

Comme pour Lodel, nous utilisons OTX dans un environnement Debian 7/8. Nous ne l'avons pas testé dans d'autres environnements. En particulier, nous ne savons pas s'il est utilisable dans un environnement Windows.


