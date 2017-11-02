Utilisateurs
------------

Les fonctionnalités seront décrites selon les besoins de chacun des utilisateurs du logiciel. Ces utilisateurs génèrent et conçoivent le site destiné aux internautes via une interface privée. Les compétences requises pour accomplir cette tâche sont disparates, ce qui implique des types de fonctionnalités très différentes, que l’on peut classer par métier.

Utilisateurs et droits d’accès
------------------------------

Lodel permet de gérer un nombre illimité d’utilisateurs, i.e. de couples identifiant / mot de passe qui permettent de démarrer une session de travail, mais ne gère pas encore les groupes d’utilisateurs (prévu pour une version ultérieure).
À chaque utilisateur est associé un rôle, lequel définit les droits d’accès aux différentes fonctionnalités du logiciel. Ainsi, un utilisateur peut être administrateur Lodel, administrateur d’un site, éditeur, rédacteur ou bien visiteur. L’interface est personnalisée en fonction de ces rôles : pour un visiteur, par exemple, certaines fonctionnalités sont inaccessibles. Lodel permet donc de personnaliser l’interface en fonction des niveaux d’utilisateurs, mais non en fonction de tel utilisateur particulier.
Chaque type d’utilisateur représente un niveau d’accès : les trois types d’administrateur peuvent déléguer une partie de leurs droits aux autres utilisateurs, qui, eux, ne peuvent pas déléguer leurs droits.
Il est prévu, dans les versions ultérieures de Lodel, de gérer plus finement les droits d’accès aux différentes fonctionnalités : il devrait être possible, pour chaque utilisateur, de spécifier les différentes fonctionnalités auxquelles il pourra accéder.

Administrateur Lodel
--------------------

Lors de l’installation de Lodel, un premier utilisateur est créé : il s’agit de l’administrateur Lodel, qui a la charge de concevoir le modèle éditorial (ME), à savoir la structure des données qui seront manipulées par les autres utilisateurs. Il est important de noter que l’affichage de ces données dans l’interface est directement dépendant de cette structure. Pour effectuer cette tâche de structuration des données, l’utilisateur dispose d’une interface privée qui atténue la difficulté technique requise par l’implémentation d’une base de données. Cette interface est codée avec un langage de templates, le Lodelscript, ce qui signifie qu’elle est modifiable par un utilisateur qui ne connaît ni PHP ni MySQL. Il incombe aussi à cet utilisateur d’administrer l’application, i.e. de jouer le rôle d’un administrateur système (gestion des utilisateurs, des droits d’accès, etc.). Pour effectuer cette tâche, il dispose d’une interface privée qui lui est propre (accessible via l’URL http://cheminVersLodel/lodeladmin).

Création, import et export de la structure des données
------------------------------------------------------

La structure et l’affichage des données sont définis dans le modèle éditorial (ME). Pour répondre à des besoins spécifiques, l’administrateur Lodel peut concevoir son propre ME. Il dispose dans Lodel de deux ME par défaut, qu’il peut utiliser tels quels ou bien modifier :

- le ME de Revues.org, conçu pour la mise en ligne de revues scientifiques spécialisées dans les sciences humaines ;
- un ME générique, qui contient tous les champs obligatoires pour fonctionner sous Lodel, ainsi que les options de configuration d’un Servoo, et qui permet donc de structurer les données selon les besoins précis de l’utilisateur.
L’administrateur Lodel dispose d’une fonctionnalité lui permettant d’exporter son ME au format SQL. Il peut en outre choisir de sauvegarder, au même moment, les templates, feuilles de style, images et scripts Javascript associés à ce ME. L’importation d’un ME sauvegardé ne peut être effectuée que lors de la création d’un nouveau site, avant qu’une seule classe n’ait été définie. Il est envisagé, pour les futures versions de Lodel, de pouvoir importer et exporter au format XML le ME, ainsi que ses éléments pris séparément (Cf. METS ?).

Structuration du ME
-------------------

Concevoir un ME consiste tout d’abord à concevoir, pour chaque site, la structure des données qui seront manipulées par les autres utilisateurs. Cette structuration s’effectue sur cinq niveaux :

- Définition des « options du site » : il faut préciser, pour chaque site, les caractéristiques nécessaires à son fonctionnement.
- Définition des « classes » : il s’agit de définir les types de contenus mis en ligne, ainsi que les index qui permettent d’établir des liens entre ces contenus. Les classes se divisent en trois grandes catégories : entités (par exemple, pour le ME de Revues.org, les publications, les textes, les images ou les liens sont autant d’entités différentes), index (de mots-clés, historique, etc.) et index de personnes.
- Définition de la structure interne des classes : les classes sont composées de différents types de champs qui permettent de caractériser précisément les différents types d’informations contenus dans une classe. Ces champs sont associés à des styles de paragraphe dans le document issu du traitement de texte.
- Définition de la hiérarchie et de l’imbrication des contenus mis en ligne : les entités peuvent être imbriquées les unes dans les autres, de manière à structurer et hiérarchiser les informations du site. Pour cela, Lodel utilise la notion de type.
- À l’intérieur même des champs, il est possible d’identifier des éléments, de manière à décrire plus finement la structure du contenu mis en ligne : pour cela, Lodel utilise deux niveaux de styles, les styles en ligne et les styles de caractères.

Premier niveau : les sites
--------------------------

L’administrateur Lodel définit, pour chaque site, les informations nécessaires à son fonctionnement : il s’agit des « options », qui sont présentées dans des groupes. On peut par exemple envisager un groupe d’options pour configurer l’accès à un Servoo pour l’import de documents, et un groupe d’options définissant les métadonnées du site. Il appartient cependant entièrement à l’administrateur Lodel de définir ses propres groupes d’options, en fonction de ses besoins. Chaque option ou groupe d’options peut être supprimé, modifié ou dupliqué. L’administrateur Lodel peut (et devrait) protéger chaque option, pour interdire ces actions aux autres utilisateurs. L’administrateur Lodel délègue le droit d’éditer le contenu des options à un autre utilisateur (typiquement l’administrateur du site), sachant qu’il peut, pour chaque option, définir le niveau d’utilisateur requis pour modifier sa valeur.

Deuxième niveau : les classes
-----------------------------

Les contenus sont appelées « entités » dans Lodel : il s’agit de contenus structurés qui peuvent être imbriqués les uns dans les autres. Ces entités peuvent être reliées entre elles par des entrées d’index linéaires ou hiérarchiques, et peuvent être liées à des entrées d’index de personnes. Entités, index et index de personnes sont appelées « classes » dans Lodel. Il est possible de créer un nombre illimité de ces trois types de classes. Deux identifiants uniques et permanents sont attribués à chaque instance d’une classe : un identifiant numérique et un identifiant textuel. Grâce à ces deux identifiants, il est possible d’attribuer à chaque objet une URL permanente (du type http://monsite/index.php?id=33 ou http://monsite/mon-bel-identifiant). L’identifiant numérique est automatiquement attribué par Lodel et ne peut pas être modifié ; l’identifiant textuel est lui aussi attribué par Lodel en fonction du titre du document, mais peut être modifié manuellement. TODO : comment sont générés les identifiants littéraux

Troisième niveau : les champs
-----------------------------

Chaque classe est constituée de champs (par exemple, un document peut être composé d’un titre, d’un corps de texte, d’images, etc.). Pour chaque champ, l’administrateur Lodel précise :

- Le groupe de champs auquel il appartient.
- Le type des données (texte, date…) : le choix d’un type a des conséquences sur l’affichage du champ dans l’interface privée, et permet à Lodel de prévoir les volumes de données manipulées et d’effectuer des contrôles lors de la saisie (contraintes de types de données et de domaines de valeurs).
- Les contraintes lors de l’édition.
- Le mode d’édition (en ligne, par import, via un éditeur WYSIWYG, etc.), avec ses éventuels paramètres.
- L’équivalent générique du champ : À DÉFINIR
- Les balises HTML autorisées pour ce champ.
- Le poids du champ dans le moteur de recherche.
- Un éventuel commentaire.

Types de champs
---------------

Lodel propose 21 types de champs.

- Texte court (tinytext en SQL) : limité à 255 caractères.
- Texte (text en SQL) : limité à 65535 caractères.
- Texte long (longtext en SQL) : plus de 4 milliards de caractères (+/- 4Go).
- Texte multilingue : champ contenant un texte traduit en plusieurs langues.
- URL : texte court, Lodel vérifiant qu’il est bien du type http://* (http pouvant être remplacé par ftp, https, file, gopher, telnet, nntp, news).
- Email : texte court, Lodel vérifiant qu’il est bien du type *@*.*.
- Nom d’utilisateur : texte court, dont le nombre de caractères doit être compris en tre 3 et 12.
- Mot de passe : texte court qui ne sera jamais affiché en clair, mais transitera en clair jusqu’à la base, où il sera stocké encrypté (MD5). Actuellement, aucune vérification sur la robustesse du mot de passe n’est effectuée (à effectuer dans une version ultérieure de Lodel).
- Entier (int en SQL) : entiers signés, codés sur 4 octets. Si aucune valeur n’est renseignée, le champ prend automatiquement la valeur 0.
- Nombre flottant (double en SQL) : nombre décimal codé sur 8 octets. Idem pour les valeurs non renseignées.
- Booléen (bool en SQL) : les deux valeurs possibles sont 0 et 1.
- Date (date en SQL) : date au format MySQL, automatiquement convertie à l’affichage dans un format lisible (jj mois aa).
- Date et heure (datetime au format SQL) : date et heure, idem pour le format.
- Heure (time en SQL) : heure, idem pour le format.
- Fichier : nom complet d’un fichier (le fichier n’est pas stocké dans la base).
- Image : nom complet d’un fichier image (l’image n’est pas stockée dans la base). Lodel vérifie que l’extension du fichier correspond bien à un format d’image.
- Couleur : champ permettant de renseigner une couleur au format hexadécimal.
- Langue : champ de type texte ne pouvant contenir que des caractères alphabétiques, et permettant la sélection de la langue du document. Une liste de langues prédéfinies est disponible, et peut être modifiée par un utilisateur avancé (les modifications s’effectuent dans le code source, et ne peuvent pas actuellemnt être effectuées dans l’interface : à prévoir dans une version ultérieure).
- Relation : champ qui permet d’établir des relations entre les entités (et entre elles seulement : ne fonctionne pas avec les index). Les relations sont unidirectionnelles : si une entité A pointe vers les entités B et C, cela ne signifie pas que B et C pointent vers A. Il est possible d’attribuer un nombre illimité de relations pour chaque document. Ce type de champ permet notamment de mettre en oeuvre un site multilingue, chaque document pouvant être relié à sa traduction.
- Liste d’items prédéfinis : ce champ permet de définir par avance l’ensemble des valeurs qu’il peut prendre (ces valeurs sont rentrées dans le champ de formulaire « Paramètres d’édition, séparés par des virgules).
- Historique : ce champ est automatiquement rempli à chaque modification (création, édition, changement de statut) d’un document. Les différentes modifications sont insérées dans l’ordre chronologique (la première au début du champ, la dernière à la fin). Ce champ permet d’obtenir la liste des modifications effectuées sur un document, mais ne constitue pas un vrai système de log.

Contraintes lors de l’édition de la valeur d’un champ
-----------------------------------------------------

À REVOIR : définition des contraintes (unique, permanent) + certaines contraintes non exclusives les unes des autres (contrairement à ce qu’il est possible de faire dans l’interface) Il est possible d’attribuer une valeur par défaut qui sera attribuée lors de la première édition d’un champ, et de paramétrer la mise à jour de ce champ lors des modifications ultérieures. Les conditions suivantes, qui sont exclusives les unes des autres, sont disponibles :

- aucune condition : le champ n’est pas requis, et n’est pas mis à jour automatiquement avec sa valeur par défaut à chaque modification ;
- champ requis : Lodel vérifie, lors de l’édition, que la valeur du champ est effectivement renseignée ; si ce n’est pas le cas, il lui attribue sa valeur par défaut, si celle-ci est indiquée, sinon, il génère un message d’erreur ; le champ n’est pas mis automatiquement à jour lors des modifications ultérieures ;
- permanent : la valeur attribuée lors de la création (valeur par défaut ou renseignée par l’utilisateur) ne peut plus être modifiée par la suite ;
- unique :???????????????

Ces contraintes sont particulièrement utiles pour la gestion des dates : en indiquant « today » dans la valeur par défaut d’un champ de type date (ou heure, ou date et heure), l’utilisateur peut s’assurer, par exemple, que la valeur initiale n’est pas modifiable s’il s’agit de la date de création d’un document (condition « unique »), ou bien que la date est automatiquement mise à jour s’il s’agit d’une date de dernière modification (condition « permanent »).

Modes d’édition des champs
--------------------------

À REVOIR : confusion dans un même champ HTML de 2 notions : champ éditable / non éditable, et modalités d’édition

Chacun des champs définis dans Lodel dispose d’un mode d’édition. Lors de la création (ou modification) d’un champ, l’administrateur Lodel associe à ce champ un mode d’édition, sachant qu’ils sont exclusifs les uns des autres. Les modes d’édition sont les suivants :

- L’édition dans l’interface, par le biais de formulaires : chacun des modes d’édition de ce type crée un champ de formulaire en HTML, que l’utilisateur peut paramétrer (choix du nombre de lignes pour un champ textarea par exemple) dans le champ de formulaire intitulé « Paramètres pour l’édition ».
- L’import d’un fichier via Servoo : le champ peut être détecté dans le document source grâce au style qui lui est associé, et une ou des fonction(s) peuvent lui être systématiquement appliqué suite à l’import.
- L’édition via un éditeur WYSIWYG (FCKEditor).

L’administrateur Lodel peut aussi décider que la valeur d’un champ n’est pas modifiable, ce qui implique que :

- sa valeur par défaut lui sera systématiquement attribuée lors de la création ;
- la mise à jour de ce champ lors des modifications ultérieures dépend de la contrainte sur les mises à jour sélectionnée.

L’administrateur Lodel décide si le nom et la valeur d’un champ non modifiable doivent être affichés dans l’interface d’édition, ou non : si non, aucun champ HTML n’est généré, pas même un champ caché.

ÉDITION DANS L’INTERFACE
------------------------

À chaque type de champ Lodel est associé un mode d’édition en ligne particulier, i.e. un type de champ de formulaire HTML.

- Texte court, texte, texte long, nom d’utilisateur, url, email, historique : si le nombre de lignes (x) est précisé dans les paramètres d’édition, une zone de texte est générée (balise <textarea rows= »x » cols= »50″>), sinon génération d’un champ de type texte (balise <input size= »50″ type= »text »>).
- Mot de passe : génération d’un champ de type password (balise <input size= »50″ type= »password »>). Aucun paramètre d’édition n’est associé à ce type.
- Booléen : génération d’une (et une seule) case à cocher (balise <input type= »checkbox »>). Aucun paramètre d’édition n’est associé à ce type.
- Entier, nombre relatif : génération d’un champ de type texte (balise <input type= »text »>). Aucun paramètre d’édition n’est associé à ces types.
- Texte multilingue : génération d’une liste déroulante à choix unique (balise <select>) permettant la sélection d’une langue, et, chaque fois qu’une langue est séléctionnée, génération d’un champ de type texte.
- Langue : génération d’une liste déroulante à choix unique (balise <select>). Aucun paramètre d’édition n’est associé à ce type.
- Liste d’items prédéfinis : il est associé à ce champ des modes d’édition qui lui sont propres : liste déroulante avec des choix multiples, liste déroulante avec un choix unique, boutons radios (choix d’une seule valeur), case à cocher (choix de plusieurs valeurs). Les différents items sont renseignés dans les paramètres d’édition, séparés par des virgules.
- Date, date et heure, heure : génération d’un champ de type texte (balise <input size= »30″ type= »text »>). Aucun paramètre d’édition n’est associé à ces types.
- Image, fichier : génération d’un tableau à une cellule, contenant deux boutons radio qui permettent de choisir le fichier sur le serveur ou en local. Il est possible, par la suite, de supprimer le fichier ou d’en choisir un autre (2 boutons radio sont ajoutés aux précédents, pour indiquer s’il faut supprimer ou conserver le fichier sélectionné lors de la dernière modification).
- Couleur : génération d’un champ de type texte de 7 caractères, destiné à recevoir la valeur hexadécimale de la couleur précédée du signe # (balise <input type= »text » size= »7″>), et d’un lien pointant vers un script Javascript qui permet de choisir une visuellement une couleur.
- Relation : génération d’une liste déroulante à choix multiples, avec un lien vers un script Javascript permettant de choisir les entités vers lesquelles pointe la relation.

IMPORT
------

L’import est réalisé via un autre système, Servoo, qui reçoit en entrée des fichiers issus d’un traitement de texte et renvoie ces fichiers au format XHTML. Les options de configuration concernant le Servoo utilisé pour convertir les fichiers d’un site se limitent aux informations de connexion (nom d’utilisateur, mot de passe, URL du serveur). Un champ qui utilise l’importation peut aussi être éditable dans l’interface de Lodel.

Quatrième niveau : les types
----------------------------

Une classe est définie par ses champs, qui décrivent la structure des données, mais aussi par les différents types d’objets qu’elle caractérise. Les types servent à :

- Définir la hiérarchie des contenus mis en ligne : chaque type peut en contenir d’autres, et ce de manière récursive (par exemple, un objet de type « publications » peut contenir un objet de type « numéro », qui peut lui-même contenir un objet de type «article», etc.).
- Définir le comportement d’un objet, et notamment d’initialiser ses différentes valeurs lors de sa création : templates associés, mode de création et statut par défaut, indexation par le moteur interne.

Pour chaque type, l’administrateur Lodel précise :

- les autres types de contenus pouvant être son parent dans la hiérarchie ;
- les 3 fichiers templates associés : À CLARIFIER ;
- le mode de création par défaut d’une occurrence de ce type (par import ou en ligne) ;
- le statut par défaut attribué à une occurrence de ce type lors de sa création(brouillon, publié, etc.) ;
- si les occurrences de ce type sont indexées par le moteur interne et référencée dans le dépôt OAI du site ;
- si les occurrences de ce type sont publiques (i.e. peuvent être créées et modifiées par un utilisateur non logué) ;
- si le type est protégé ou non ;
- son mode d’affichage dans l’interface (plié, déplié, fonctions avancées).

Cinquième niveau : les styles
-----------------------------

Lodel utilise trois niveaux de styles, pour définir les parties d’une entité selon une granularité plus ou moins fine.

Styles associés aux champs du ME
--------------------------------

L’administrateur Lodel associe à chaque champ du ME un ou plusieurs style(s). Ce style sert à repérer dans le document source issu d’un traitement de texte les différents blocs correspondant aux différents champs du ME. Le rédacteur, qui importe les documents dans Lodel, aura la charge d’utiliser de manière unique chacun de ces styles dans les documents source (par exemple, un titre de document, un bloc de texte, un bloc de mots-clés, etc.).

Styles internes
---------------

Par ailleurs, il est possible de définir des styles dits « internes », qui servent à identifier les différents éléments à l’intérieur d’un bloc de texte (par exemple les niveaux de titre dans le corps du texte). Ces styles permettent de repérer la structure interne des blocs de texte : ils correspondent aux styles de paragraphe dans un traitement de texte.

Styles de caractères
--------------------

Enfin, il est possible de définir des « styles de caractères » pour pouvoir identifier des termes au sein des éléments définis par les styles internes : ces styles sont particulièrement utiles pour assigner une signification particulière à certains termes (par exemple une citation), et pour repérer les entrées d’index qui sont disséminées dans le document (et non regroupées dans un bloc de texte correspondant à un champ).

TODO : expliquer style « gourmand »

Affichage des données
---------------------

Les données sont affichées de manières différentes, en fonction des manipulations qui doivent être effectuées dessus. On distingue principalement :

- les modes de création : typiquement réservés à l’administrateur Lodel, ces modes permettent la création de classes ou d’options ;
- les modes d’éditions : typiquement réservés à l’administrateur d’un site (pour les options) ou au rédacteur, ces modes permettent de créer ou modifier les valeurs des champs définis par l’administrateur Lodel ;
- le mode de navigation : destiné à générer les pages visibles dans l’interface publique.

Création des templates
----------------------

Lorsque la structure des données a été définie, il reste à déterminer la manière dont ces données seront affichées : pour cela, l’administrateur créé des templates en Lodelscript, qui permettent de générer dynamiquement des pages Web. Lors de l’installation d’un ME prédéfini, un certain nombre de templates sont disponibles. L’administrateur Lodel associe à chaque type d’entité, d’index ou index de personnes deux templates, qui permettent de paramétrer leur affichage d’une part dans l’interface d’administration et d’autre part dans l’interface publique. Ces templates sont codés en Lodelscript (TODO : annexe décrivant les nouveautés du Lodelscript 0.8).

Le Lodelscript permet :

- l’extraction des données contenues dans la base avec des requêtes SQL simplifiées (jointures automatiques) ;
- l’utilisation des boucles et des conditions ;
- la réutilisation de code dans divers templates via un système de macros ;
- l’utilisation de fonctions prédéfinies (filtres) pour traiter les variables à l’affichage ;
- l’intégration de code PHP au sein du code Lodelscript.

Moteur de recherche
-------------------

Un moteur de recherche est disponible pour chaque site. Cette fonctionnalité est primordiale pour l’internaute, dont le but est souvent de trouver le plus rapidement possible l’information qu’il recherche. Elle est aussi nécessaire pour tous les autres types d’utilisateurs, qui peuvent avoir occasionnellement, voire souvent si les données manipulées sont volumineuses, ce même besoin.

Cette fonctionnalité est utilisable des deux manières suivantes :

- recherche simple : l’utilisateur spécifie quelques mots-clés ;
- recherche avancée : l’utilisateur spécifie, en plus des mots-clés, les types de documents et les champs sur lesquels doit porter la requête.

Il est possible d’utiliser des caractères jocker ainsi que des opérateurs logiques pour préciser une requête.

Afin répondre à des exigences de performance, la fonctionnalité de recherche repose sur un index. Cet index est construit et mis à jour automatiquement à chaque ajout, modification ou suppression d’une entité, d’une entrée d’index ou d’index de personnes. Il faut donc définir au préalable, pour chaque champ d’une classe, s’il est indexé ou non, et son poids (1, 2, 4 ou 8, plus le nombre étant élevé, et plus le champs a de poids), et pour chaque type d’une classe si les documents de ce type sont indexés ou non.

Parser et générer des flux RSS
------------------------------

Afin de permettre l’alimentation d’un site Web avec les informations d’un autre site, Lodel fournit des fonctions Lodelscript qui parsent et génèrent des flux RSS 0.9, RSS 1.0, RSS2 et Atom 0.3 (parser RSS Magpie).

Administration système
----------------------

Après avoir mis en place le modèle éditorial, l’administrateur Lodel peut accomplir les tâches d’administration suivantes : gestion des utilisateurs et des sites, sauvegarde des données.

Administration des utilisateurs
-------------------------------

L’ administrateur Lodel peut ajouter d’autres utilisateurs globaux, qui seront eux aussi des administrateurs Lodel. Il a bien évidemment aussi le droit d’administrer les utilisateurs d’un site, mais il délègue ce droit aux administrateurs de site. Ainsi, chaque administrateur Lodel a la possibilité de créer, modifier, copier ou supprimer les autres administrateurs Lodel. Lors de la suppression d’un utilisateur, celui est définitivement supprimé, et non stocké temporairement dans une corbeille.

Administration des sites
------------------------

L’administrateur Lodel peut ajouter, modifier, supprimer / restaurer, ou encore bloquer (i.e. empêcher le site d’être visible par un utilisateur non authentifié) un site. La suppression d’un site consiste à le mettre dans une corbeille, d’où la possibilité de le restaurer par la suite.

Sauvegarde des données
----------------------

L’administrateur Lodel peut sauvegarder l’ensemble des données stockées dans la base de données (structure et contenu des sites), avec, optionnellement, tous les fichiers associés (documents annexes, images, etc.). Les données sont sauvegardées dans une archive qui contient le fichier SQL décrivant la structure de la base, ainsi que les données contenues dans chacune des tables. L’utilisateur pourra décompresser cette archive lors d’une nouvelle installation de Lodel. L’administrateur Lodel peut en outre télécharger le schéma XML de chaque classe de son ME. L’importation d’un tel fichier pour insérer une classe dans un ME n’est cependant pas encore possible.

Administration d’un site
------------------------

Lorsqu’il crée un site, l’administrateur Lodel a la possibilité de (et devrait) créer un utilisateur chargé d’administrer le site.

Gestion des utilisateurs du site
--------------------------------

L’administrateur d’un site a la possibilité de créer, dupliquer, modifier et supprimer un utilisateur. À chaque utilisateur est attribué un certain nombre de droits sur le site, comme défini plus haut. L’administrateur d’un site peut en outre consulter l’historique des sessions ouvertes par un utilisateur, et purger cet historique.

Gestion des options techniques du site
--------------------------------------

L’administrateur d’un site est chargé de renseigner les options qui ont été définies, pour le site, par l’administrateur Lodel.

Sauvegarde des données
----------------------

L’administrateur peut à tout moment exporter les données et leur structure (i.e. la base de données correspondant au site, au format SQL). Inversement, l’administrateur peut importer, à partir de l’interface, ces mêmes données pour recréer le site. Lors de la sauvegarde, l’administrateur peut choisir de ne télécharger que la base de données, sans les fichiers externes.

Éditeur
-------

La principale tâche de l’éditeur consiste à décider de l’opportunité de publier ou non un document. Publier un document, dans Lodel, signifie le rendre visible dans l’interface publique. À chaque document est attribué un statut, qui détermine si le document est :

- « verrouillé » : ???????
- non publiable en l’état (statut « brouillon ») : le document ne peut pas être publié, même si le(s) document(s) parents le sont ;
- « prêt à publier » (par défaut pour tout nouveau document) : le document peut être publié à tout instant, y compris par l’intermédiaire d’un document parent ;
- « publié pour l’intranet » : comprendre publié pour les amis, i.e. le document est visible dans une partie privée de l’interface publique (authentification requise pour un internaute). Ce statut n’est pas implémenté dans la version 0.8.
- « publié » : le document est visible dans les deux interfaces, par tous les utilisateurs, et peut être dépublié à tout instant, y compris par l’intermédiaire d’un document parent ;
- « publié protégé » : le document est visible dans les deux interfaces, et ne peut pas être dépublié, même si le(s) document(s) parents le sont.

Le fait de publier un document implique que tous les documents qu’il contient sont aussi instantanément publiés. Même chose pour la dépublication. C’est la raison pour laquelle les deux statuts « brouillon » et « publié protégé » sont nécessaires, pour éviter des publications ou des dépublications intempestives.

Rédacteur
---------

La principale tâche du rédacteur consiste à importer du contenu dans Lodel. Ce contenu comprend les divers documents, mais aussi les méta-données décrivant ces documents, ainsi que les entrées d’index permettant d’établir des liens entre ces documents.

Saisie des informations
-----------------------

Pour importer du contenu dans Lodel, le rédacteur dispose principalement de deux possibilités :

- l’import, à partir de documents issus d’un traitement de texte, qui sont convertis au format XHTML par Servoo avant d’être importés dans Lodel ;
- l’édition en ligne, par le biais de formulaires où chaque champ représente un élément du document : tous les champs de la classe correspondant au document à importer sont présents dans le formulaire.

Il est en outre possible, pour un utilisateur, d’importer des documents par mail (en les envoyant en pièce jointe à une adresse déterminée) ou par FTP, si les documents sont volumineux (en les copiant dans le répertoire d’import de Lodel). La taille maximale des fichiers pouvant être importés dans l’interface est définie par la configuration de PHP (option post_max_size).

Le contenu saisi par le rédacteur correspond aux champs définis dans le ME par l’administrateur Lodel : il comprend donc théoriquement le contenu à proprement parler, mais aussi les métadonnées qui décrivent ce contenu, ainsi que les entrées d’index et d’index de personnes.

Contrôle des informations saisies
---------------------------------

Quel que soit le mode d’importation, un contrôle de la validité des informations saisies avec la définition des éléments du modèle est effectué. En effet, tout document, avant d’être inséré dans la base de données, est affiché dans un formulaire, ce qui permet :

- à Lodel de vérifier que tous les champs obligatoires sont renseignés et, que, pour chaque champ, les contraintes de types de données et de valeurs sont bien respectées ;
- à l’utilisateur de vérifier que tous les éléments de son document ont bien été reconnus, et sont donc associés aux champs adéquats, et d’effectuer les corrections nécessaires.

Ce formulaire de saisie du document conforme est généré automatiquement, et se modifie en fonction des caractéristiques propres d’un document qui ne sont pas définis dans le modèle (éléments optionnels ou définis comme pouvant être multiples).

Contrôle de l’intégrité des données
-----------------------------------

Avant l’insertion des données dans la base, Lodel contrôle l’intégrité référentielle des données (unicité des entrées d’index ou des identifiants littéraux, etc.)

Visiteur
--------

Le visiteur ne peut rien faire d’autre qu’afficher les documents, quel que soit leur statut.
