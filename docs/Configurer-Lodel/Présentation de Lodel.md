Qu’est-ce-que Lodel ?
---------------------

Lodel permet d’éditer en ligne des revues sans connaissances informatiques poussées : la maîtrise des outils bureautiques courants (traitement de texte, navigateur internet) suffit à maîtriser le processus de mise en ligne.

Lodel est un logiciel d’édition électronique : il prend en charge le processus de publication des textes, depuis le traitement de texte de l’utilisateur, jusqu’à la mise en ligne.

Il ne gère pas le secrétariat de rédaction en amont (expertise scientifique des articles, conférences de rédaction, correction), mais peut apporter une aide, notamment en offrant différents types d’accès, avec des droits différents, selon les types d’utilisateurs.

Son rôle devient en revanche central pour la deuxième partie du travail éditorial jusqu’à la mise en ligne :

• conversion des textes d’un format traitement de texte à un format web,

• maintenance des publications,

• gestion de la périodicité des publications et de l’hétérogénéité des types de publication.

• Il génère en outre automatiquement l’ensemble des métadonnées dont les publications ont besoin pour être correctement identifiées, indexées et référencées, notamment par les moteurs de recherche.

• Enfin, Lodel permet de prendre en compte les relations entre publication électronique et publication papier des mêmes textes.

Créé à l’origine pour des revues scientifiques, il permet d’importer automatiquement des listes de sommaires pour la publication électronique rétroactive, mais aussi de gérer la mise en ligne différée du texte intégral.

Séparation de la forme et du fond
---------------------------------

Lodel appartient à une génération de logiciels de publications en ligne généralement appelés systèmes de gestion de contenu (ou CMS, voir FAQ). Ces logiciels ont pour point commun de reposer sur une séparation dans la gestion du contenu et de sa mise en forme.

Cette séparation n’existait pas dans les publications papier – où le texte n’existe pas sans son actualisation matérielle – ni dans le langage HTML, qui est un langage de mise en forme de contenu.

Fonctionnement

Les problèmes posés par l’absence de séparation entre forme et contenu dans le contexte d’une publication électronique (notamment lorsqu’il s’agit de traiter des masses importantes de documents) ont encouragé le développement de systèmes comme Lodel séparant nettement ces deux éléments en s’appuyant sur un triptyque composé de :

• Un document source

• Un entrepôt où est stocké le contenu « brut »

• Un « moule » ou maquette qui donne des instructions de mise en forme pour toute représentation du contenu.

Pour des raisons historiques, les documents sources sont en général produits par un traitement de texte. La structuration du texte à ce niveau est importante. Elle s’effectue, pour Lodel, par l’intermédiaire d’un modèle de document utilisable dans le traitement de texte.

L’entrepôt où repose le contenu brut est un dossier dans lequel sont stockés les fichiers XML, couplé à une base de données relationnelle MySQL.

La maquette est enfin un fichier HTML particulier, qui mélange langage HTML pur et instructions particulières écrites dans un langage de script. Lodel appelle ces maquettes des templates, et le langage donnant des instructions, le Lodelscript [– qui s’appuie lui-même sur du PHP. (Pour en savoir plus, voir la rubrique…)]

Lors de la requête d’un utilisateur, le template génère une page HTML, la nourrit du contenu qu’il aura extrait de la base de données et des fichiers XML de contenu, et la met en forme selon les instructions écrites par le maquettiste.

On imagine bien qu’il n’existe donc pas un seul template pour tout un site. Chaque template est défini pour une situation de lecture particulière : lecture d’un article en texte intégral, consultation du sommaire d’un dossier ou d’un numéro, consultation des index et pour un type particulier de document : article, recension, textes de présentation.

Pourquoi séparer la forme du fond ?

Le principe de séparation du contenu et des éléments de mise en forme pour une reconstitution à la volée de la publication est aujourd’hui largement utilisé. Il permet en effet de conserver les textes indépendamment de leur mise en forme, qui peut par la suite évoluer de manière rapide et indépendante.

Il permet par ailleurs de décliner un même contenu sur plusieurs supports, selon les besoins, sans avoir à dupliquer l’information, ce qui rendrait sa maintenance plus compliquée.

D’un point de vue fonctionnel, il permet de distinguer les rôles. Le secrétaire de rédaction ne doit plus avoir de compétence en HTML, puisque cet élément est entièrement géré par la maquette. Celle-ci peut être conçue par un maquettiste spécialisé qui ne devra pas avoir de compétence en matière de secrétariat de rédaction.

Autre avantage non négligeable, le maquettiste n’intervient qu’une seule fois sur le site. Il n’est pas sollicité lors de la mise en ligne de nouveaux contenus, tandis que le secrétaire de rédaction peut se concentrer sur les étapes de la mise en ligne des textes, sans se soucier de l’organisation de l’information sur le site.

La séparation de la forme et du contenu dans le processus de publication électronique constitue un progrès considérable par rapport au schéma de publication traditionnel :

• changer la charte graphique du site revient à changer le template et cela met à jour toutes les pages du site ;

• ajouter une page ne consiste plus qu’à en écrire le contenu.

Une plus grande pérennité des documents est ainsi assurée, dans la mesure où le contenu, proprement structuré, pourra être indéfiniment réutilisé pour de nouvelles publications sans nouvelle saisie. Enfin, elle permet aux documents de rester indépendants du contexte particulier de leur publication. Le lieu, le moment et la technologie de publication, l’identité de l’éditeur peuvent ne plus constituer des obstacles à la communication des documents, pour peu que ceux-ci s’insèrent dans une structure logique similaire ou compatible avec les autres.

Du traitement de texte à la mise en ligne
-----------------------------------------

Vue sous l’angle d’un secrétaire de rédaction, la publication d’un texte prend donc la forme suivante : Le texte est structuré dans Word ou sur tout autre traitement de texte, par l’intermédiaire d’un modèle de document.

Le document produit est alors traité par Lodel pour être décomposé en unités sémantiques : les métadonnées sont placées dans la base de données, le corps de texte du document lui-même est structuré par un balisage XML.

Enfin, lorsqu’un lecteur appelle un document, il interroge le template, qui va extraire l’information de la base de données, la mettre en forme selon les instructions lodelcript qu’il contient, et restituer finalement un document HTML classique –mais généré dynamiquement [voir lexique], à l’utilisateur.

La continuité de cette chaîne de publication implique une correspondance entre les modèles utilisés sur les différentes plate-formes : continuité entre le modèle de document utilisé pour structurer le document dans le traitement de texte, le schéma XML pour produire le fichier XML de référence, et la maquette permettant de mettre en forme.


Un point de départ : le traitement de texte de l’utilisateur

Le traitement de texte est le point de départ inévitable de la chaîne de publication en édition, électronique ou non. C’est donc sur ce support qu’il faut effectuer la première partie du travail, celle qui consiste à identifier les différents éléments d’un document : Titre, intertitre, corps de texte, illustrations, légendes.

Lodel repose sur le parti pris d’insérer dans le document lui-même tous les renseignement qui le concerne : mots-clés pour les index, résumés, nom de l’auteur, etc. Il faut aussi marquer la nature de ces renseignements d’une manière informatique. Dans le logiciel de traitement de texte, cela passe par l’imposition d’un style sur chaque type d’élément contenu par le document : style « normal » pour le corps de texte, style « titre 1 » pour les intertitres de premier niveau, etc. L’ensemble des styles utilisés par Lodel sont rassemblés dans un modèle de document à partir duquel chaque nouveau document doit être créé. Les documents ainsi produits sont enregistrés au format rtf, doc, ou même sxw .

Le nœud du problème de la publication électronique est le passage du traitement de texte à des formats adaptés à d’autres supports, comme le web. Lodel permet aux utilisateurs de s’appuyer sur la suite logicielle libre Open Office pour effectuer cette conversion. Open Office a en effet la particularité d’utiliser le langage XML comme format pivot de sauvegarde de ses documents, et de pouvoir être piloté automatiquement en mode serveur par des scripts. La conversion d’un document n’est donc pas prise en charge par l’utilisateur, mais par un serveur Open Office qui importe le document d’origine, interprète les styles de paragraphe et de caractère qu’il contient, et l’exporte dans Lodel enfin sous un format XML.

Pour l’utilisateur, le traitement par Open Office de son document s’effectue via une interface web qui lui permet de charger le fichier source sur le serveur, de déclencher l’opération de transformation, de vérifier le résultat produit et de corriger les erreurs s’il y a lieu. Il lui est possible d’ailleurs, de se passer du serveur Open Office et d’entrer du code XHTML directement dans une fenêtre de formulaire web.

Une interface web pour piloter le chargement du document et organiser la publication

Un site de publication géré par Lodel dispose d’un espace privé, une interface d’édition, protégée par contrôle d’accès, réservé aux rédacteurs et administrateurs. L’interface d’édition, c’est un peu l’« arrière-boutique » d’un site ; c’est un espace dont l’accès est réservé aux rédacteurs, éditeurs et administrateurs du site, leur permettant de gérer la préparation des textes et le flux de publication sur le site. Après authentification, l’utilisateur, peut dont charger via l’interface d’édition, le fichier produit par le traitement de texte et vérifier si les styles qu’il a appliqués à son document sont correctement interprétés par Lodel.

Il lui reste à vérifier l’exactitude de ses métadonnées et à les corriger le cas échéant avant de valider. Le document validé est par défaut invisible pour le public. A cette étape du traitement, les documents sont présents sur le serveur, prêts à être publiés. Ils doivent encore être organisés et faire l’objet d’une décision formelle de publication.

Dans Lodel, l’organisation des documents est prise en charge dans la même interface d’édition que pour leur chargement. Cette interface permet de créer plusieurs types de publications et de les emboîter les unes dans les autres, un peu comme des dossiers, jusqu’à l’unité éditoriale minimale qui est le document. La généricité du module de publication est presque totale car il est possible d’organiser en toute liberté le modèle éditorial du site lors de sa création. Concrètement, l’administrateur Lodel a la possibilité d’utiliser un modèle éditorial existant (comme celui qu’utilise Revues.org) ou d’en créer un qui lui est totalement personnel en définissant manuellement le nombre de champs qu’il va utiliser, leur organisation, l’intitulé et les propriétés de chacun d’eux. Cette possibilité donne au logiciel une puissance considérable puisqu’elle lui permet de s’adapter à un grand nombre de cas.

La contrepartie de cette liberté est qu’elle requiert un haut niveau de maîtrise et une certaine expérience du processus de publication électronique. C’est pourquoi il existe des modèles préconçus capables de satisfaire des besoins de publication classiques. Ces modèles doivent être chargés à la création du site ; mais rien n’empêche de les faire évoluer par la suite en créant de nouveaux champs ou en modifiant les propriétés de ceux qui existent. Seul l’administrateur Lodel est habilité à effectuer ce type de modification car les conséquences de la modification du modèle éditorial sont graves et il est impossible de revenir en arrière.

Le résultat : la publication
----------------------------

L’interface d’édition de Lodel permet de « voir » les nouvelles publications telles qu’elles apparaîtront aux yeux du public, sans que ces changements soient encore visibles par tous.

Une fois que l’ensemble des publications est bien en place, un bouton « Publier » permet de basculer l’ensemble des modifications en interface publique.

L’intérêt d’utiliser une technologie dynamique de publication de contenu apparaît à ce niveau. Ce type de système permet en effet de faire en sorte que la publication d’un nouveau document déclenche toute une série d’événements sans manipulation particulière : génération du même document en différents formats (format impression, PDF), mise à jour des sommaires et des index (auteurs, mots-clés), etc. Ainsi, avec un minimum de manipulation, l’information contextuelle est toujours adaptée au contenu principal de la page qui s’affiche.


Publier aussi pour les robots

Un document est destiné à être lu, bien sûr. Mais avant d’en arriver là, il doit être référencé, signalé, trouvé. Or ce travail de mise en valeur d’une publication, qui permet au document de trouver ses lecteurs passe souvent par un dialogue avec des robots documentaires chargés de collecter, de trier et de présenter les documents susceptible d’intéresser les lecteurs.

Des métadonnées pour les moteurs de recherche

Lodel permet de générer automatiquement une liste de métadonnées dans l’en-tête des fichiers HTML à partir des renseignements qui ont été donnés au niveau du traitement de texte. Par défaut, les métadonnées suivent la norme Dublin Core : elles sont indiquées sous cette forme dans le code source de la page web : <meta name= »DC.Title, Subject, Creator, Date, Language…

Les métadonnées fournies dans l’en-tête HTML servent aux robots d’indexation qu’utilisent les moteurs de recherche.

Utiliser au mieux les métadonnées dans un document HTML, c’est avoir de bonnes chances d’être bien référencé dans les principaux moteurs. C’est encore plus vrai pour les moteurs spécialisés qui utilisent souvent le standard Dublin Core de description de métadonnées.

Des flux de données pour la nouvelle génération du web

Les moteurs de recherche ont une fonction utile mais particulière : ils permettent ou bien de répérer l’ensemble des documents disponibles sur un sujet donné, ou bien de retrouver un document particulier. Totalement insensibles à toute dimension temporelle des activités de publication, ils sont de très mauvais outils pour se tenir au courant de l’actualité d’un domaine, c’est-à-dire des dernières publications le concernant.

C’est à ce besoin que répondent les fichiers RSS ou Atom, qui sont lus par des logiciels clients spécifiques. Lodel fournit en standard ce type de format d’information, permettant aux lecteurs d’être immédiatement avertis des mises à jour du site. Les fichiers RSS sont par ailleurs souvent utilisés par les portails ou d’autres sites proches, pour agréger les flux d’information et fournir un service de veille à leur public.

OAI : un outil de communication pour les communautés scientifiques

Lodel est doté de scripts lui permettant de répondre aux requêtes de type « OAI-PMH ». L’Open Archives Initiative Protocol for Metadata Harvesting (OAI-PMH) est un protocole qui vise à faciliter l’échange et la valorisation d’archives numériques. Elle permet à des fournisseurs de services de moissonner des métadonnées sur les sites de fournisseurs de données. Il est ainsi possible d’utiliser un protocole OAI pour créer un outil de recherche simultanée dans plusieurs catalogues de bibliothèques.Ce protocole, basé sur XML et le Dublin Core permet l’échange de métadonnées entre fournisseurs de données et fournisseurs de services.

En premier lieu, l’OAI-PMH repose sur la distinction entre « data providers » et « service providers ». Les premiers sont des bases de documents, des « archives » au sens très particulier où l’OAI utilise ce terme, les seconds sont des sortes de moteurs de recherche qui permettent aux utilisateurs de chercher une information en explorant plusieurs bases de documents simultanément. Dans le jargon de l’OAI, ce sont des « harvesters ». Le grand avantage de cette architecture de distribution de l’information est que la recherche devient totalement indépendante de l’organisation des bases de documents. Que l’on cherche dans une seule grosse base ou mille petites, le résultat est le même pour l’utilisateur, puisque sa requête est traitée par un « harvester » qui agit pour son compte auprès de l’ensemble des bases qu’il connaît (ou uniquement de celles choisies par l’utilisateur).

Le système n’a, en soi, rien de révolutionnaire. Cela fait plusieurs années que la notion de « métamoteur » et de requête multi-bases existe. Ce qui est plus original, c’est que le protocole promu par l’Open Archives Initative est ouvert; il ne se conçoit pas à l’intérieur de l’espace clos d’une seule institution, mais doit permettre à toutes les bases de communiquer. Une des missions essentielles de l’OAI est de diffuser des outils permettant à des institutions et collectifs, même de petite taille, de mettre en ligne des bases de documents interrogeables par OAI-PMH. En intégrant des scripts OAI dans sa propre architecture de fonctionnement, Lodel participe de ce mouvement d’ouverture.
