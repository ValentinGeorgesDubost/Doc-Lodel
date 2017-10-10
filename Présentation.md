1.  Qu'est-ce que Lodel ?
-------------------------

Lodel est un logiciel d’édition électronique simple d'utilisation et adaptable à des usages particuliers.
Il appartient à la famille des gestionnaires de contenus (en anglais, Content management system, CMS) et s’est spécialisé dans l’édition de textes longs et complexes dans un environnement éditorial très structuré.
Pour une présentation générale de Lodel, visitez lodel.org.
Lodel est un logiciel libre.
Il est développé à 99.9% par le Cléo qui produit les plateformes d'OpenEdition (dont Revues.org, OpenEdition Books, Calenda). Notre équipe est réduite et a beaucoup évolué ces dernières années.
Nous disposons de peu de temps pour répondre aux questions posées sur la liste.
Nous remercions au passage tous les abonnés qui prennent le temps de proposer des réponses.
Lodel est peu documenté.
Lire le code et les logs d'erreur est souvent la seule méthode pour résoudre les problèmes.
Pour lire les logs d'erreurs, il faut y avoir accès, ce qui n'est pas toujours le cas dans les hébergements mutualisés.
Lodel n'est pas bien "packagé".
Nous l'utilisons au Cléo sous Debian, mais nous n'avons pas testé d'autres environnements d'installation.
Dans d'autres configurations, il est possible que des adaptations soient nécessaires.
Lodel existe depuis longtemps. La base de Lodel date de la première moitié des années 2000.
Il a évolué sur cette base. Il est daté, en particulier dans sa conception et dans certaines librairies utilisées (pear par exemple).
Donc pour résumer, la prise en main n'est pas simple et il faut disposer de compétences informatiques et de persévérance pour l'utiliser...
Le Cléo produit pour la plateforme Revues.org des sites de revues basés sur Lodel, mais le site revues.org comprend aussi des services qui ne sont pas produits par Lodel : entrepôt OAI, moteur de recherche, versions pdf et epubs des articles notamment.
Ces fonctionnalités sont développées avec d'autres technologies. Vous ne les trouverez pas dans Lodel.

2.  OTX
-------

OTX est l'application qui permet la conversion de fichiers de traitement de texte stylés en fichiers XML-TEI compatibles avec le modèle éditorial "Revues.org" distribué dans Lodel.
Le projet d'écriture de l'application OTX prévoyait au départ une totale adaptabilité d'OTX au modèle éditorial de Lodel.
En spécifiant des informations sous forme de XPath dans le modèle éditorial du site Lodel, OTX devait être capable de convertir le document de traitement de texte stylé en XML TEI sur la base de ce XPath.
Concrètement, OTX n'est que partiellement dynamique.
Certaines spécifications de XPath dans le modèle éditorial de Lodel sont prises en compte par OTX, d'autres non.
La liste des cas non-reconnus n'est pas documentée. Nous avons choisi de publier Lodel 1.0 et OTX 1.0 malgré cette limite.
Le Cléo ne propose pas de service de conversion ouvert comme c'était le cas avec ServOO (le prédécesseur d'OTX, logiciel de conversion utilisé avec Lodel 0.8/0.9). Pour importer des documents de traitement de texte, il faut donc installer aussi OTX.
Comme pour Lodel, nous utilisons OTX dans un environnement Debian 7/8. Nous ne l'avons pas testé dans d'autres environnements.
En particulier, nous ne savons pas s'il est utilisable dans un environnement Windows.

3.  Lodel pour OpenEdition: Maison des revues
---------------------------------------------

La maison des revues http://maisondesrevues.org/ est le site d'accompagnement éditorial des revues de Revues.org qui publient sur la plateforme avec Lodel mais bénéficient également des autres services cités plus haut (pdf, epub, oai, maquette...).
Donc cette documentation contient des informations relatives à Lodel mais aussi des informations relatives à d'autres services de la plateforme.
N'hésitez pas à nous contacter pour toute question sur ce logiciel et l'édition électronique ouverte, merci !
