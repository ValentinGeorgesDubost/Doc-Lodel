Lodel
=====

Interface côté édition
----------------------

L’interface côté édition est l’interface qui permet de faire des modifications de contenu dans la revue (ajouter un document, un article…). Cette interface n’est accessible qu’aux personnes en charge de l’édition de la revue. Certains milieux utilisent le mot » back office » pour désigner ce type d’espace.

Interface côté site
-------------------

L’interface côté site est le site de la revue tel qu’il apparaît à l’internaute. Il est accessible à tous. Certains milieux utilisent le mot « front office » pour désigner ce type d’espace.

Migration
---------

Transfert des données et adaptation de leur mise en forme en vue de leur exploitation par au autre système de traitement des données. Par exemple, migration des données exploitées par la version 0.7 de lodel vers la version 0.8.

Macro
------

Dans lodel, les macros sont des scripts écrits en lodelscript qui permettent l’affichage d’une séquence d’instructions au moyen d’un identifiant simple. Une macro définit un identifiant qui sera remplacée dans la page par le script définit dans la macro.

Modèle éditorial Lodel
----------------------

Le modèle éditorial (ME) définit les types de publication et de document utilisables dans Lodel que les différents champs à renseigner dans la base de données. Les modèles éditoriaux sont entièrement modifiables et personnalisables en fonction de l’utilisation souhaitée de lodel. Il est ainsi possible d’adapter Lodel à des types de publication très variées. Revues.org ne gère, en revanche, qu’un seul ME par version de lodel. Des variations mineures peuvent cependant exister entre les revues, soit en raison de l’histoire (le ME mûrit progressivement), soit en raison de particularité de la revue, essentiellement du point de vue des index (chaque revue peut disposer de types d’index spécifiques).
Groupe de gestion : Cf.  https://lodeldevel.revues.org/

Maquettes
=========

Lodelia
-------

Maquette générique de revue développée par Revues.org comprenant les templates, les CSS et les macros. Elle est basée sur le modèle éditorial de Revues.org. Revues.org a connu deux générations de Lodelia :

- Première génération de Lodelia (2002-2007) : Lodelia bleue, Lodelia rouge, Lodelia verte, Raspaillette. Cette génération s'appuie sur une matrice commune, qui est ensuite "forkée". Il est impossible de rétablir le lien avec la matrice. Il y a donc une parenté entre la matrice et les maquettes qui en découlent, mais le lien entre elles est rompu.

- Deuxième génération de Lodelia (2007-...) : Lodelia 1.0 pour Lodel 0.7 (2007) / Lodelia 2.0 pour Lodel 0.8 (2007). C’est une maquette commune, gérée par SVN. Cela signifie que les modifications réalisées sur la maquette sont appliquées immédiatement à toutes les revues utilisant cette maquette. Seuls les CSS diffèrent d'une revue à l'autre. Ainsi, les méthodes de développement sont appliquées aux créations de maquettes. A terme, 90% des maquettes de revues devraient être gérées via des Lodelia 2.0.

Lodelscript
-----------

Langage de template propre à lodel. Il est basé sur php et MySQL. Il permet de réaliser des maquettes de sites dynamiques, c'est-à-dire des maquettes qui font références à des informations contenues dans une base de données. Il ne nécessite pas de connaissances approfondies des langages php et MySQL.

Maquette graphique
------------------

La maquette graphique d’un site est ce qui définit l'apparence, l'ordonnancement des contenus et l'ergonomie du site. Elle est implémentée via un jeu de fichiers templates et de feuilles de style css. Elle détermine l’architecture du site et la mise en forme des données. La maquette comprend les templates (définition des contenus affichés sur la page) et les CSS (mise en forme des contenus). Les revues sur Revues.org ont généralement pour maquette une simple colorisation de la Lodelia générique. Certaines revues, notamment les plus anciennes, bénéficient parfois de maquettes au graphisme plus élaboré, conçu par une équipe de graphistes externe.
Exemple de simple colorisation : http://questionsdecommunication.revues.org/
Exemple de maquette graphique élaborée : http://gradhiva.revues.org/

Fil d’Ariane
------------

Élément de navigation d’un site permettant de visualiser dans quel niveau hiérarchique du site la page en cours se situe. Cet élément de navigation est cliquable pour faciliter la navigation. Exemple : partie 1 > sous-partie1.3 > sous-partie1.3.2 > document 1

Barre de navigation
-------------------

Partie de l’interface d’un site composée de liens permettant d’accéder aux différents documents publiés dans le site.
+ constante + souvent à gauche + tjrs présente.

Barre d’outils éditoriale
-------------------------

Elle permet de modifier la mise en forme d'un article soit sur la page (modification de la taille des caractères) soit pour un usage différent (formatage pour l'impression, fac-similé, signaler par courriel). Dans la Lodelia 1, elle est située sous la barre de navigation de l'article.

Pied de page
------------

Barre de navigation et d'information affichée en pied de page de toutes les pages d’un site renvoyant à des informations techniques et pratiques.
Pour la Lodelia 1.0 utilisée par Revues.org, ce pied de page contient les liens et mentions suivantes : Plan du site - À propos - Contacts - Crédits - ISSN électronique : xxxx-xxxx, Nous adhérons à Revues.org - Édité avec Lodel - Flux de syndication.

Stylage
=======

Modèle de document bureautique
------------------------------

Un modèle bureautique est un document qui contient des styles. Il sert de base aux nouveaux documents créés. Le modèle de document Word Revues.org contient les définitions des styles compréhensibles par Lodel.
Feuille de style (bureautique) : Une feuille de style contient la liste, le nom et la description formelle (mise en forme) des styles employés dans un document. Les styles ont une fonction d’harmonisation de la mise en forme du document (tous les paragraphes stylés en « Titre 1 » auront la même mise en forme). Les styles ont aussi une fonction sémantique, exploitée par Lodel : ils qualifient les paragraphes. Cela permet par exemple de constituer automatiquement des sommaires (à partir de tous les paragraphes stylé en « Titre X ») ou des index.

Feuille de style (CSS)
----------------------

L'un des objectifs majeurs de CSS est de proposer une stylisation indépendante de la structure du document. La maquette, par exemple, ne décrit que l'architecture interne, tandis que CSS décrit tous les aspects de la présentation : mise en forme des paragraphes, des caractères, position des blocs de textes ou images. Elles peuvent être intégrées dans le document html (dans la balise <head>) mais on les définit généralement dans un fichier externe (xxx.css) que l'on appelle depuis toutes les pages du site. Cela permet d'avoir une seule feuille de style pour tout le site et d'homogénéiser sa mise en forme. On peut cependant définir plusieurs feuilles de style pour plusieurs types d’affichage du même site (par exemple, une mise en forme « consultation du site » et une mise en forme « impression ».

Mise en forme locale
--------------------

Une mise en forme locale dans un logiciel de traitement de texte est un attribut formel (couleur, taille, forme de police etc.) appliqué à un paragraphe ou une chaine de caractères. Contrairement aux styles, cet attribut supplémentaire ne porte pas sur un type générique de paragraphe (titre, notes de bas de page...) mais sur un mot ou un paragraphe, il est donc local. On applique par exemple une mise en forme locale « italique » sur le titre d'un ouvrage. Pour un document destiné à être importé dans Lodel, les mises en forme locales sont à proscrire sauf si elles sont motivées pas une décision éditoriale.
Exemples :

- il faut mettre en italique le titre d'un ouvrage ou une locution latine.
-	il ne faut pas augmenter la taille de la police du style « titre1 » en y ajoutant une mise en forme local « corps 36pt ». Si on veut que les « titre1 » s'affichent, dans Word, avec un corps 36pt il faut changer l'attribut « corps » du style « titre1 ». + côté site (css)
-	cf. précis de stylage.

Information scientifique
========================

Libre Accès (Open Access)
-------------------------

Mouvement de l’Open Access : naît au début des années 1990 pour favoriser la communication scientifique et remédier à la “crise des périodiques scientifiques” (augmentation du prix des abonnements). Réunit chercheurs, éditeurs, bibliothécaires pour promouvoir le libre accès à l’information scientifique. Trois conférences fondatrices : Budapest, Bethesda, Berlin, donnent lieu à des déclarations publiques qui définissent le libre accès et lui assignent des objectifs politiques (“les 3 B”). 
Le chercheur britannique Stevan Harnad a popularisé la distinction entre deux “voies” du libre accès :

- Le Green Open Access : le dépôt par les chercheurs eux-mêmes de leurs publications dans des “archives ouvertes”
- Le Gold Open Access : la création de publications (essentiellement des revues) en libre accès. 

Le chercheur américain Peter Suber a proposé d’autres déclinaison du terme “libre accès” :

- Gratis Open Access : accès libre à l’information mais sans droit de réutiliser ni rediffuser
- Libre Open Access : accès libre accompagné d’une licence libre autorisant réutilisation et diffusion (conforme aux déclarations des 3B)

Modèles économiques de l’édition en libre accès

Auteur-payeur : Dans le Gold Open Access, le modèle économique dominant est le modèle “auteur-payeur” où le chercheur paie les frais à la revue dans laquelle il publie les frais d’édition de son article (“article processing charges” ou APC).
Freemium : un modèle alternatif est le modèle freemium que met en oeuvre OpenEdition : ni l’auteur ni le lecteur ne paie les coûts de publication, mais ceux-ci sont partiellement couverts par la commercialisation de services à valeur ajoutée (premium) sur la base de contenus en libre accès (free).

Interopérabilité
================

XML
---

XML, eXtensible Markup Language, est un langage descriptif, s'appuyant sur des balises, permettant de structurer des contenus. Il permet d’organiser des données. C’est un format ouvert qui permet l’utilisation des données dans différents contextes ou avec différentes applications (interopérabilité). Par exemple au flux RSS est conforme à un schéma XML, ce qui lui permet d’être interprété dans n’importe quel agrégateur de flux ou d’être utilisé pour la syndication de contenu.
La structure d'un document XML est définissable et validable par un schéma (anciennement : DTD).
XML schema, DTD : Un document DTD, XML schema est un document permettant de définir un modèle de structure pour un certain nombre de documents XML. Il permet notamment de vérifier la validité de ce document. Un document XML schema est lui-même un document XML alors que DTD utilise une syntaxe spécifique.

TEI
---

La TEI que l'on pourrait traduire par groupe d'initiative pour le balisage normalisé des textes est une norme de balisage, de notation et d'échange de corpus des documents électroniques fondée sur le SGML. Elle s'est élaborée pragmatiquement à partir des besoins de structuration, de conceptualisation et de mise en réseau de textes."
Plus simplement, la DTD TEI, fondée à l'origine sur le SGML et s'appuyant désormais sur le XML, est un langage de marquage qui permet d'échanger des données textuelles, notamment pour les sciences humaines et les études sur les textes littéraires. Une version allégée dite TEI Lite contient les définitions des éléments les plus couramment utilisés.
Ses éléments recouvrent toutes les spécificités littéraires, qu'elles concernent le document lui même (paragraphes, strophes, chapitres, notes de bas de page, etc.) ou qu'elles lui soient extérieures (commentaire éditorial, interprétation, analyse, etc.).
Source : http://blogokat.canalblog.com/archives/2004/12/20/220271.html

Métadonnées
-----------

Les métadonnées sont des informations attachées à un document qui permettent de le qualifier. Des métadonnées peuvent être attachés à n’importe quel type de document (texte, image, son, vidéo…). Elles servent à faciliter la recherche d'information, faciliter l'interopérabilité, faciliter la gestion et l'archivage, gérer et protéger les droits. Exemples de métadonnées : auteur, titre, type de document.
Il existe des standards de métadonnées. Les métadonnées lodel sont conformes au standard dublincore ce qui facilite interopérabilité des informations éditées avec lodel.

Syndication de contenu
----------------------

La syndication de contenu sur internet consiste à afficher sur un site des informations qui se trouvent sur un autre site qui les rend disponible (dans un flux rss par exemple). C’est par ce procédé qu’on peut afficher les informations scientifiques de Calenda sur le site d’une revue.
Agrégation : L’agrégation de contenu est un procédé d’affichage de plusieurs flux de syndication en même temps. Un agrégateur de contenu peut être intégrer sur une page d’un site internet. Il existe aussi des applications dédiées (RSS Bandit, RSS reader…). L’agrégation de contenus est mise en oeuvre sur les carnets “radar” d’Hypothèses.

HTACCESS
--------

Les fichiers htaccess sont utilisés pour filtrer les accès à un dossier sur un serveur.
Les fichiers .htaccess sont des fichiers de configuration des serveurs web Apache. Ils peuvent être placés dans n'importe quel répertoire du site web. Ils servent à modifier les droits d'accès, créer des redirections, écrire des messages d'erreur personnalisés.

Protocoles
----------

OAI :
- L’OAI (Open Archives Initiatives) est un projet international qui vise à faciliter l'échange et la valorisation d'archives numériques. Elle permet de créer un outil de recherche simultanée dans plusieurs catalogues de bibliothèques. Il se base sur un protocole d’échange de métadonnées, OAI-PMH (Open Archives Initiative Protocol for Metadata Harvesting).
Définition simple et précise : http://blogokat.canalblog.com/archives/oai_pmh_pas_a_pas/index.html
Depot OAI : Revues.org dispose d’un dépôt OAI, c'est-à-dire une base de données interrogeable via le protocole OAI-PMH. Les documents édités pas Revues.org sont donc potentiellement accessibles depuis tous les systèmes de recherche utilisant le protocole OAI-PMH.

METS (Metadata Encoding and Transmission Standard) :
Schéma XML autorisant la création et la description intégrale (données descriptives, administratives et structurelles) d'objets numériques textuels ou graphiques. Destiné particulièrement aux échanges entre institutions patrimoniales, METS est conforme aux recommandations de OAIS (Open Archival Information System) et est maintenu actuellement par la Bibliothèque du Congrès. METS fera sans doute assez rapidement l'objet d'une norme ISO.
Un document METS est composé de cinq parties distinctes :
- descriptive metadata
- administrative metadata
-	file group
-	structural map
-	behaviour
