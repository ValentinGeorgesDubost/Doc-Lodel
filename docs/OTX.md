OTX
===

OTX est l'application qui permet la conversion de fichiers de traitement de texte stylés en fichiers XML-TEI compatibles avec le modèle éditorial "Revues.org" distribué dans Lodel. Le projet d'écriture de l'application OTX prévoyait au départ une totale adaptabilité d'OTX au modèle éditorial de Lodel. En spécifiant des informations sous forme de XPath dans le modèle éditorial du site Lodel, OTX devait être capable de convertir le document de traitement de texte stylé en XML TEI sur la base de ce XPath. Concrètement, OTX n'est que partiellement dynamique. Certaines spécifications de XPath dans le modèle éditorial de Lodel sont prises en compte par OTX, d'autres non. La liste des cas non-reconnus n'est pas documentée. Nous avons choisi de publier Lodel 1.0 et OTX 1.0 malgré cette limite.

Le Cléo ne propose pas de service de conversion ouvert comme c'était le cas avec ServOO (le prédécesseur d'OTX, logiciel de conversion utilisé avec Lodel 0.8/0.9). Pour importer des documents de traitement de texte, il faut donc installer aussi OTX.

Comme pour Lodel, nous utilisons OTX dans un environnement Debian 7/8. Nous ne l'avons pas testé dans d'autres environnements. En particulier, nous ne savons pas s'il est utilisable dans un environnement Windows.

Plus d'informations : <https://github.com/OpenEdition/OTX>

Schema TEI OpenEdition
======================

Ce projet versionne le schéma TEI utilisé sur les plateformes d'OpenEdition Revues.org et OpenEdition Books.
Il correspond au modèle éditorial revuesorg distribué avec Lodel <https://github.com/OpenEdition/lodel>

Parmi les standards d'encodage XML d'un texte, TEI ([Text Encoding Initiative](<http://www.tei-c.org/>)) est sans doute le plus complet et le plus mûr. TEI définie plus de 500 composants textuels et concepts différents (mots, phrases, caractère, symbole, personne, etc.). Une utilisation personalisée d'un schéma TEI implique une customisation du schéma à ses spécificités, pour s'adapter et réduire la richesse de TEI au schéma restreint (donc simplifié) voulu. La communauté TEI a crée un langage de spécification nommé ODD [("One Document Does it all")](http://www.tei-c.org/Guidelines/Customization/odds.xml) pour modifier le schéma TEI générique. Avec une description ODD, il est possible grâce à un outil nommé Roma de générer de manière automatique des schémas TEI customisés (xsd, relaxNG, etc.) et de la documentation.
Dans ce projet, le dossier odd contiens la description ODD, et le dossier xsd contiens le schéma xsd généré par roma.

Pour valider un fichier XML avec ce schéma, il est possible d'utiliser le schéma en local ou d'utiliser le schéma xsd publié à l'adresse <http://lodel.org/ns> (se reporter au répertoire /doc pour un exemple de déclaration du schéma dans le fichier xml).

Se reporter aux releases (<https://github.com/OpenEdition/tei.openedition/releases>) pour connaitre les évolutions du schéma.

Les recommandations d'usage sont décrites avec des exemples dans le wiki du projet (<https://github.com/OpenEdition/tei.openedition/wiki>)
