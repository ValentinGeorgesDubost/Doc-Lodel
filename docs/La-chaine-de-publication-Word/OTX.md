OTX
===

OTX est l'application qui permet la conversion de fichiers de traitement de texte stylés en fichiers XML-TEI compatibles avec le modèle éditorial "OpenEdition Journal" distribué dans Lodel. Le projet d'écriture de l'application OTX prévoyait au départ une totale adaptabilité d'OTX au modèle éditorial de Lodel. En spécifiant des informations sous forme de XPath dans le modèle éditorial du site Lodel, OTX devait être capable de convertir le document de traitement de texte stylé en XML TEI sur la base de ce XPath. Concrètement, OTX n'est que partiellement dynamique. Certaines spécifications de XPath dans le modèle éditorial de Lodel sont prises en compte par OTX, d'autres non. La liste des cas non-reconnus n'est pas documentée. Nous avons choisi de publier Lodel 1.0 et OTX 1.0 malgré cette limite.

Le Cléo ne propose pas de service de conversion ouvert comme c'était le cas avec ServOO (le prédécesseur d'OTX, logiciel de conversion utilisé avec Lodel 0.8/0.9). Pour importer des documents de traitement de texte, il faut donc installer aussi OTX.

Comme pour Lodel, nous utilisons OTX dans un environnement Debian 7/8. Nous ne l'avons pas testé dans d'autres environnements. En particulier, nous ne savons pas s'il est utilisable dans un environnement Windows.

Plus d'informations : <https://github.com/OpenEdition/OTX>
