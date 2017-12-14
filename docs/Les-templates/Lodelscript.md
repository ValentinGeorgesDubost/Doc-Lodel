LODELSCRIPT
===========

- [Préface](#préface)
  - [À propos](#À-propos)
  - [Prérequis](#prérequis)
  - [Notations](#notations)
  - [Principe de fonctionnement](#principe-de-fonctionnement)
- [Variables](#Variables)
  - [Définition d'un variable](#définition-dun-variable)
  - [Variables globales](#variables-globales)
  - [Débuggage](#débuggage)
  - [Variables de traduction](#variables-de-traduction)
- [Tableaux](#tableaux)
- [Commentaires](#commentaires)
- [Conditions](#conditions)
  - [Syntaxe](#syntaxe)
  - [Conditions simples](#conditions-simples)
  - [Conditions complexes](#conditions-complexes)
  - [Conditions utilisant les expressions régulières](#conditions-utilisant-les-expressions-régulières)
  - [Switch](#switch)
- [Boucles](#boucles)
  - [Boucle foreach](#boucle-foreach)
  - [Boucles base de données](#boucles-base-de-données)
    - [Quelques exemples : pour les familiers de SQL](#quelques-exemples--pour-les-familiers-de-sql)
    - [Syntaxe normale : LOOP, TABLE, WHERE, ORDER, LIMIT](#syntaxe-normale--loop-table-where-order-limit)
    - [Pagination des résultats : SPLIT](#pagination-des-résultats--split)
    - [2 variables renvoyées par les boucles : COUNT, NBRESULTS](#2-variables-renvoyées-par-les-boucles--count-nbresults)
    - [Débuggage : SHOWSQL](#débuggage--showsql)
    - [Utilisation de iddocument, idperson et identry dans la clause WHERE](#utilisation-de-iddocument-idperson-et-identry-dans-la-clause-where)
    - [Commandes avancées : GROUPBY, SELECT, HAVING](#commandes-avancées--groupby-select-having)
    - [Combinaisons (AND, OR)](#combinaisons-and-or)
  - [Possibilités d'affichage évoluées dans les boucles](#possibilités-daffichage-évoluées-dans-les-boucles)
    - [Alternative](#alternative)
    - [Dofirst & Dolast](#dofirst--dolast)
    - [Before & After](#before--after)
  - [Boucles prédéfinies ](#boucles-prédéfinies-)
    - [La boucle TOC](#la-boucle-toc)
    - [Les liens PREVIOUS / NEXT](#les-liens-previous--next)
    - [Les listes suivants / précédents](#les-listes-suivants--précédents)
    - [La boucle EXTRAIT_IMAGES](#la-boucle-extrait_images)
    - [La boucle PARAGRAPHES](#la-boucle-paragraphes)
    - [La boucle RSS](#la-boucle-rss)
- [Modification des variables : fonctions filtres ou pipes](#modification-des-variables--fonctions-filtres-ou-pipes)
  - [Filtres PHP et développements](#filtres-php-et-développements)
  - [Combinaisons de modificateurs de variables](#combinaisons-de-modificateurs-de-variables)
- [Macros et fonctions](#macros-et-fonctions)
  - [Macros](#macros)
  - [Fonctions](#fonctions)
  - [Inclusion de fichiers template](#inclusion-de-fichiers-template)
- [Intégrer PHP à Lodelscript](#intégrer-php-à-lodelscript)
  - [PHP dans lodelscript](#php-dans-lodelscript)
  - [La gestion du cache : BLOCK, ESCAPE et REFRESH](#la-gestion-du-cache--block-escape-et-refresh)
- [Jeu de caractères](#jeu-de-caractères)
- [Multilinguisme](#multilinguisme)
- [Liste des messages d'erreur](#liste-des-messages-derreur)
  - [Messages renvoyés par le parseur LodelScript](#messages-renvoyés-par-le-parseur-lodelscript)
  - [Messages renvoyés par le parseur PHP ou SQL](#messages-renvoyés-par-le-parseur-php-ou-sql)
- [Les tags wiki par défauts](#les-tags-wiki-par-défauts)
  - [de types bloc](#de-types-bloc)
  - [de type inline](#de-type-inline)


------------------------


# Préface
## À propos
Cette documentation a été rédigée par Julien Dubuc.
Version initiale : 0.1 appliquée à Lodelscript 0.5 pour Lodel 0.5.
Date de création : 05 mai 2003
Contributeurs :
* Ghislain Picard pour l'adaptation à la version 0.6 ;
* Ghislain Picard, François Lermigeaux, Gautier Poupeau pour l'adaptation à la version 0.7 (mars 2004).
* Sophie Malafosse pour l'adaptation à la version 0.8 (janvier 2007).
* Pierre-Alain Mignot pour l'adaptation à la version >= 0.8.1 (juillet 2008).
* Jean-François Rivière (mise à jour 2014).

## Prérequis
Pour lire cette documentation, il est nécessaire de connaître assez bien les langages de mise en page sur internet : HTML, XHTML. Des notions de CSS sont aussi importantes. Enfin, pour aller plus loin, il est bon de connaître les rudiments de SQL, mais cela n'est pas nécessaire.

## Notations
Quelques conventions de notations sont utilisées dans cette documentation. Les exemples de code sont signalés dans un cadre. Un texte en gras avant une portion de code indique la nature du code :
* **variables** : les variables et leurs valeurs utilisées pour l’exemple.
* **template** : le fichier template
* **résultat** : le code HTML généré

Lorsque la syntaxe indiquée pour utiliser une instruction comporte des parties en italique cela signifie que ces parties sont optionnelles.

## Principe de fonctionnement
LodelScript est un langage de template qui est composé de balises HTML classiques et de code de plus haut niveau spécifique à LodelScript, comme des variables ou des boucles. Ce langage permet de définir l’aspect graphique d’un site dynamique sans pour autant connaître de langage de programmation et de langage d’interrogation de bases de données comme SQL.

Lodelscript a été développé parallèlement au logiciel Lodel, mais peut très bien être adapté à d'autres systèmes de gestion des données. Cette documentation fera souvent référence à Lodel, si vous utilisez lodelscript dans un autre contexte, il vous faudra adapter quelques exemples.

La syntaxe de LodelScript s’appuie sur un système de balises comparable au XML et a été inspirée par SPIP et d'autres langages de template.

Les balises sont écrites en MAJUSCULES et se distinguent ainsi du code xhtml composé en minuscules :

    <p>
    <IF COND="[#AUTEUR]">
       Cet article a été écrit par [#AUTEUR] et publié le [#DATE]
    </IF>
    </p>

Ce code sera interprété et permettra de générer une page dynamiquement :

    <p>Cet article a été écrit par Frédéric Bertrand et publié le 14 juillet 1934.</p>

Techniquement, au premier accès à une page, le fichier template correspondant est transformé en code PHP. Le code PHP est ensuite exécuté puis conservé en cache tant que le fichier de template n’a pas été modifié. Pour les accès suivants à la page, le code PHP sera directement exécuté ou son résultat sera pris dans le cache.

# Variables

Cinq types de variables peuvent être distinguées dans le lodelscript :

* les variables natives ou définies par la modélisation par défaut de la base de données ; ces variables sont les mêmes pour tous les utilisateurs de lodel ;
* les variables définies par le modèle éditorial du site ; elles dépendent donc du modèle éditorial ;
* les variables définies par l'utilisateur dans le système des options du site dans l'interface d'administration de lodel et utilisables dans tous les templates du site ;
* les variables dont la valeur est assignée dans le template par la commande LET.
* les variables de traduction qui permettent la traduction de l'interface de navigation (lodel 0.8+)

Si vous le souhaitez, vous pouvez utiliser le système des options du site dans l'interface d'administration de Lodel, pour attribuer une valeur fixe à une variable. Ces variables sont définies dans des groupes, et accessibles dans les templates de la manière suivante :
    `[#OPTIONS.NOM_GROUPE.NOM_VARIABLE]`

Dans le cadre de l'utilisation normale de Lodel les variables les plus courantes sont automatiquement disponibles dans les maquettes en fonction du contexte. Ainsi, si vous visualisez un document, en y accédant par `index.php?id=12`, alors la variable `[#TITRE]` donnera le titre du document consulté.

Pour afficher une variable dans un template il faut utiliser la syntaxe suivante :

    [#MAVARIABLE]

Les noms de variables ne peuvent contenir que des lettres majuscules, des chiffres ou le caractère ‘_’. Les minuscules, les lettres accentuées, le point (.) et le tiret (-) sont interdits.

Exemple :

**variables** :

	[#TITRE] :
	valeur : La migration des cigognes

**template** :

	<html>
	   <head>
		  <title>[#TITRE]</title>
	   </head>
	   <body>
		  ...
	   </body>
	</html>


**résultat** :

	<html>
	   <head>
		  <title>La migration des cigognes </title>
	   </head>
	   <body>
		  ...
	   </body>
	</html>


Certaines variables peuvent être disponibles dans la base de données « Lodel » en plusieurs langues (champs de type MLTEXT ou MLLONGTEXT. Dans ce cas, pour afficher une variable, il faut faire suivre le nom de la variable de deux points (:) et de deux lettres représentant la langue désirée suivant la norme ISO 3166-1.

Pour afficher la version française de la variable RESUME :
	[#RESUME:FR]

Pour afficher la version anglaise de la variable RESUME :
	[#RESUME:EN]


## Définition d'un variable
Il est également possible d’assigner des valeurs aux variables directement dans le fichier template en utilisant la syntaxe suivante :

	<LET VAR="NOMVARIABLE">valeur</LET>

La valeur peut contenir du code HTML et du code LodelScript :

**variables** :

	[#TYPE] :
	article


**template** :

	<LET VAR="MESSAGE">
	   <IF COND="[#TYPE] EQ 'article'">
		  <em>Article</em>
	   <ELSE/>
		  <em>Document</em>
	   </IF>
	</LET>

	[#MESSAGE] publié le [#DATEPUBLI].


**résultat** :

	<em>Article</em> publié le 21/08/1962

**N.B.** : la syntaxe `[avant(#VARIABLE)après]` n'est plus valide en 0.8. Pour afficher le texte seulement si `#VARIABLE` n'est pas vide, il faut désormais utiliser la syntaxe des tests avec la commande `<IF>` ou bien encore les possibilités ouvertes par `<ALTERNATIVE>`.
Les variables sont définies localement, c'est-à-dire qu'un variable définie dans une boucle ne sera accessible qu'à l'intérieur de celle-ci. Pour accéder à une variable définie dans une boucle hors de celle-ci il faut utilise un variable globale/

## Variables globales
Depuis Lodel 0.9, il est possible de définir et d'accéder aux variables globales du context, par exemple pour accéder à une variable récupérées dans une boucle à l'extérieure de celle-ci. 

On définit une variable globale en ajoutant un attribut `GLOBAL="1"` à l'élément `<LET>`.

Un variable globale est accessible de la même manière qu'une variable locale mais en utilisant le symbole `%` à la place de `#` : `[%NOM_VARIABLE]`.

**template** :

	<LOOP NAME="getParentEntity" SELECT="idparent" TABLE="entities" WHERE="id='[#ID]'">
	   <LET VAR="parent" GLOBAL="1">[#IDPARENT]</LET>
	</LOOP>

	L'idparent de l'entité est [%PARENT].

## Débuggage
Toutes les variables Lodelscript sont disponibles dans un tableau php $context. 
Donc en ajoutant dans le template 
```
	<?php
	  var_dump($context);
	?>
```
on peut vérifier les variables Lodelscript disponibles.



## Variables de traduction
Les variables de traductions (traductions de tous les éléments d'interfaces définis dans la maquette) sont éditables dans l'interface d'administration de Lodel : onglet administration > administrer les traductions du site. On peut ajouter des traductions du site dans différentes langues + renseigner les traductions de toutes les variables dans ces langues.

Pour créer une variable de langue dans un template (fichiers contenus dans le répertoire tpl/ du site Lodel), il suffit de l'appeler en utilisant la syntaxe suivante : `[@MA_VARIABLE_TRADUCTION]`. Une fois la variable de traduction ajoutée dans le template, il suffit de se rendre dans l'interface d'administration de Lodel onglet administration > administrer les traductions du site et de cliquer sur le lien "Rechercher toutes les variables dans tous les templates".

La variable Lodelscript `[#SITELANG]` contient la langue de navigation du site (par défaut prend la valeur définie comme langue principale dans les métadonnées du site : onglet administration  > options du site)
En fonction de la variable `[#SITELANG]` Lodel utilisera la valeur des variables de traductions dans la langue correspondante.

# Tableaux

Depuis Lodel 0.9, il est possible  d'utiliser l'attribut ARRAY avec l'élément LET pour créer des tableaux :

**variable :**

	On suppose ce tableau préexistant : [#LANGUAGES]
	array('fr', 'en', 'es', 'de')


**template** :

	<LET ARRAY="langues">[#LANGUAGES]</LET>
	<LOOP NAME="foreach" ARRAY="[#LANGUES]">
	   - [#VALUE]<br />
	</LOOP>


**résultat** :

	- fr 
	- en 
	- es 
	- de


Il est possible de définir une clé pour une entrée de tableau en utilisant la syntaxe suivante : `<LET ARRAY="myarray.mykey">myvalue</LET>`

A défaut de clé explicite, une clé numérique sera générée automatiquement : `<LET ARRAY="myarray[]">myvalue</LET>`

Pour accéder à un élément d'un tableau, il faut utiliser la syntaxe suivante : `[#MYARRAY.MYKEY]`

**template** :

	<LET ARRAY="langues[]">french</LET>
	<LET ARRAY="langues.en">english</LET>
	[#LANGUES|var_dump]<br/>
	- [#LANGUES.0]<br/>
	- [#LANGUES.EN]<br/>


**résultat** :

	array(2) { [0]=> string(6) "french" ["en"]=> string(7) "english"}
	- french
	- english


Une tableau peut être défini de manière locale ou globale (en utilisant l'attribut `GLOBAL="1"`) de la même manière que pour les variables.

# Commentaires

Pour insérer des commentaires dans le fichier template, il faut utiliser la syntaxe suivante :

	<!--[ Ceci est un commentaire.
	Il est possible d’utiliser plusieurs lignes ]--> 

Ces commentaires n’apparaissent pas dans la page HTML qui sera générée à partir du fichier template et visible par l'internaute. Si pour une raison ou une autre vous souhaitez que les commentaires soient visibles dans le source du document publié, utilisez les commentaires HTML normaux :

	<!-- blabla -->


# Conditions
## Syntaxe

L’instruction `<IF>` permet d’exécuter une partie du template si une certaine condition est remplie. Ici la variable 'test' est un entier pouvant être égale à 0, 1 ou une autre valeur.


	<IF COND="[#TEST] EQ 1">
	   code à exécuter si la variable test est égale à 1
	<ELSEIF COND="[#TEST] EQ 0"/>
	   code à exécuter si la variable test est égale à 0
	<ELSE />
	   code à exécuter si la variable test est égale à une autre valeur
	</IF>

Note : les blocs `<ELSEIF />` et `<ELSE/>` sont facultatifs.

## Conditions simples

Les conditions sont composées d’une ou deux variables ou constantes et d’un opérateur.

**variable :**

	[#TYPE] :
	article


**template** :

	<IF COND="[#TYPE] EQ 'article'">
	   C’est un article.
	<ELSEIF COND="[#TYPE] EQ 'rubrique'">
	   C’est une rubrique.
	<ELSE/>
	   Ce n’est ni un article ni une rubrique.
	</IF>


**résultat** :

	C’est un article.


Il existe plusieurs opérateurs :

* `var1 EQ var2 (==)` : Vrai si var1 est égal à var2
* `var1 NE var2 (!=)` : Vrai si var1 n'est pas égal à var2
* `var1 GT var2 (>)` : Vrai si var1 est supérieur à var2
* `var1 LT var2 (<)` : Vrai si var1 est inférieur à var2
* `var1 GE var2 (>=)` : Vrai si var1 est supérieur ou égal à var2
* `var1 LE var2 (<=)` : Vrai si var1 est inférieur ou égal à var2
* `var1 % var2` : Vrai si var1 n'est pas divisible par var2
* `!var1` : Vrai si var1 est vide, égale à zéro ou à faux (inverse donc la condition : vrai devient faux et faux devient vrai).
* `var1` Vrai si var1 n’est pas vide ou est différente de zéro
* `var1 AND var2` Vrai si var1 et var2 sont vraies (toutes les deux)
* `var1 OR var2` Vrai si var1 ou var2 sont vraies (au moins une des deux)
* `var1 LIKE /lodel\-\d+/` : vrai si var1 matche 'lodel-[0-9]' (expression régulières)
* `var1 SEQ var2 (===)` : Vrai si var1 est égal à var2 et est du même type
* `var1 SNE var2 (!==)` : Vrai si var1 n'est pas égal à var2 en fonction du type

Note : var1 et var2 peuvent être des variables [#VAR] ou bien des constantes sous forme de nombres ou sous forme de chaînes de caractères. Les chaînes de caractères doivent être entourées de guillemets simples : 'article'

Exemples

	<IF COND="[#STATUS] GT '0'">
	   Ce document est publié et consultable.
	</IF>



	<IF COND="[#TITRE]">
	   Il y a un titre et il n'est pas vide.
	</IF>



	<IF COND="[#COUNT] % 2">
	   La variable est paire.
	<ELSE/>
	   La variable est impaire.
	</IF>



## Conditions complexes

Il est possible de combiner plusieurs opérateurs afin d’obtenir des conditions plus évoluées. Il est conseillé de mettre entre parenthèses chaque condition simple afin d’éviter les problèmes de priorité des opérateurs et de gagner en lisibilité.

	<IF COND="([#TYPE] EQ 'article') OR ([#TYPE] EQ 'compte-rendu')">
	   Ce document est un article ou un compte-rendu.
	</IF>


	<IF COND="(([#COUNT] GT 0) AND ([#COUNT] LE 10)) OR ([#MAX] GT 15)">
	   La variable COUNT est comprise entre 0 et 10 ou bien la variable MAX est supérieure à 15.
	</IF>


## Conditions utilisant les expressions régulières

Il peut être utile de comparer une valeur en utilisant des expressions régulières. Pour ceci, il faut utiliser le mot clé 'LIKE' et encadrer l'expression régulière. La recherche ne prend pas compte de la casse.

**variable :**

	[#TYPE] :
	fichierannexe


**condition :**

	<IF COND="[#TYPE] LIKE /^[a-z]annexe$/">
	   Cette entité est un document annexe.
	<ELSE />
	   Cette entité n'est pas un document annexe.
	</IF>


**résultat** :

	Cette entité est un document annexe.

Lors de l'utilisation de l'opérateur 'LIKE' dans une condition '<IF>', Lodelscript renverra un tableau [#MATCHES] contenant 
* comme premier élément un tableau contenant toutes les occurences correspondant à l'expression régulière, 
* comme deuxième élément un tableau contenant toutes les occurences "capturées" par les premières parenthèses, 
* comme troisième élément un tableau contenant toutes les occurences "capturées" par les deuxièmes parenthèses, 
* etc.

**Exemples**

    <LET VAR="test">ceci est un test du tableau MATCHES</LET>
    <IF COND="[#TEST] LIKE /^(.*?) un test du (.*?)$/">
      [#MATCHES.0.0]<br /> <!-- ceci est un test du tableau MATCHES -->
      [#MATCHES.1.0]<br /> <!-- ceci est un -->
      [#MATCHES.2.0]<br /><!-- tableau MATCHES -->
      <pre>[#MATCHES|var_dump]</pre>
    </IF>

Affichera

    array (size=3)  
	0 => array (size=1)
		0 => string 'ceci est un test du tableau MATCHES' (length=35)  
	1 => array (size=1)
		0 =>  string 'ceci est' (length=8)  
	2 => array (size=1)
		0 =>  string 'tableau MATCHES' (length=15)

On peut l'utiliser pour récupérer les langues d'un champ multilingue. Supposons que [#RESUME] est un champ multilingue qui contient 3 langues :

    <IF COND="[#RESUME] LIKE /<r2r:ml lang=\"([a-z]+)\"/">
      <pre>[#MATCHES|var_dump]</pre>
    </IF>

Affichera :

    array (size=2)
	0 => array (size=3)      
		0 => string '<r2r:ml lang="fr"' (length=17)      
		1 => string '<r2r:ml lang="es"' (length=17)
		2 => string '<r2r:ml lang="en"' (length=17)  
	1 =>  array (size=3) 
		0 => string 'fr' (length=2)  
		1 => string 'es' (length=2) 
		2 => string 'en' (length=2)


## Switch
Cette condition est similaire au Switch de PHP. La syntaxe est la suivante :

	<SWITCH TEST="[#TYPE]"> // test du switch sur la variable [#TYPE]
	   <DO CASE="article">
		  // code si [#TYPE] == "article"
	   </DO>
	   <DO CASE="rubrique">
		  // code si [#TYPE] == "rubrique"
	   </DO>
	   <DO CASES="collection, numero">
		  // code si [#TYPE] == (collection || numero)
	   </DO>
	   <DO CASE="default">
		  // code à executer si aucun condition n'est vérifiée
	   </DO>
	</SWITCH>


# Boucles

Les boucles permettent d’exécuter plusieurs fois une opération avec des variables dont les valeurs peuvent changer à chaque passage. Les valeurs de ces variables peuvent être extraites de la base de données directement (cas des boucles base de données) ou bien générées par une fonction PHP prédéfinie par un développeur (cas des boucles prédéfinies).

Ces variables sont locales à la boucle, c'est-à-dire qu’elles ne sont pas accessibles en dehors de la boucle et masquent les variables de même nom qui auraient été définies avant la boucle.

## Boucle foreach
Cette boucle est similaire à celle de PHP. Les clés du tableau sont passées dans la variable `key` et les valeurs dans la variable `value`.
L'exemple suivant va afficher les résumés dans différentes langues (on suppose que la variable 'language' est un tableau contenant des langues (`français=>fr, english=>en, español=>es, deutsch=>de`)) :

	<LOOP NAME="foreach" ARRAY="[#LANGUAGE]">
	   <IF COND="[#RESUME:#VALUE]">
		  [#KEY]<br/>
		  [#RESUME:#VALUE]
	   </IF>
	</LOOP>


## Boucles base de données
### Quelques exemples : pour les familiers de SQL

Les boucles base de données permettent d’extraire les données directement de la base de données et s’utilisent comme le montrent les exemples suivants. Ces exemples sont repris et commentés dans la section suivante.

Une boucle montrant tous les enregistrements présents dans la table "textes", i.e. tous les documents appartenant à la classe intitulée "textes".

	<LOOP NAME="tous_les_textes" TABLE="textes">
	   <DO>
		  <br />- [#TITRE], publié le [#DATEPUBLI].
	   </DO>
	</LOOP>


Une boucle montrant tous les documents appartenant à la classe "textes" ET qui sont publiés.

	<LOOP NAME="tous_les_textes_publies" TABLE="textes" WHERE="status GT 0">
	   <DO>
		  <br />- [#TITRE], publié le [#DATEPUBLI].
	   </DO>
	</LOOP>


Ou bien si on ne veut que les documents publiés ET du type 'article' :

	<LOOP NAME="tous_les_articles_publies" TABLE="textes" WHERE="status GT 0" WHERE="type EQ 'article'">
	   <DO>
		  <br />- [#TITRE], publié le [#DATEPUBLI].
	   </DO>
	</LOOP>


Si on souhaite, de plus, les classer par date descendante (DESC) :

	<LOOP NAME="tous_les_articles_publies_par_date" TABLE="textes" WHERE="status GT 0" WHERE="type EQ 'article'" ORDER="datepubli DESC">
	   <DO>
		  <br />- [#TITRE], publié le [#DATEPUBLI].
	   </DO>
	</LOOP>


Si on souhaite afficher les 10 derniers articles publiés, classés par date descendante :

	<LOOP NAME="10_derniers_articles_publies_par_date" TABLE="textes" WHERE="status GT 0" WHERE="type EQ 'article'" ORDER="datepubli DESC" LIMIT="0,10">
	   <DO>
		  <br />- [#TITRE], publié le [#DATEPUBLI].
	   </DO>
	</LOOP>


### Syntaxe normale : LOOP, TABLE, WHERE, ORDER, LIMIT

Le corps de la boucle est compris entre les balises `<DO>` et `</DO>`, c'est cette partie qui sera affichée à chaque passage de la boucle.

L’attribut NAME est obligatoire et unique, c'est-à-dire dans un même fichier template deux boucles ne peuvent pas avoir le même nom (attention, si deux boucles ont le même nom, dans deux fichiers différents, mais inclus dans le même template, alors il y aura une erreur). Pensez à donner un nom explicite à cet attribut, il permettra de bien indiquer à quoi sert cette boucle et quelle est sa fonction.

L’attribut TABLE permet de définir de quelles tables doivent être extraites les données. A priori, le développeur de template pour Lodel utilise les tables définies par le modèle éditorial (ME). Par exemple, pour le ME de OpenEdition Journals, les tables suivantes sont disponibles :
* Tables stockant les entités (publications et documents) : publications, textes, textessimples, individus, fichiers, liens.
* Tables stockant les entrées d'index : indexes, indexavances.
* Tables stockant les entrées d'index de personnes : auteurs.

Si la requête fait appel à plusieurs tables, il faut répéter autant de fois que nécessaire cette attribut. Il faut au moins définir une table.

Une boucle montrant tous les textes présents dans la base.

	<LOOP NAME="tous_les_textes" TABLE="textes">
	   <DO>
		  <br />- [#TITRE], publié le [#DATEPUBLI].
	   </DO>
	</LOOP>


La partie comprise entre `<DO>` et `</DO>` va s'afficher à chaque fois que la boucle rencontrera un enregistrement dans la base de données Lodel. S'il y en a 43, elle affichera 43 fois quelque chose comme :

	<br />- Le titre de l'article, publié le 03/12/2003.


L’attribut `WHERE` permet de spécifier les critères que devront remplir les informations pour être extraites. Si plusieurs attributs `WHERE` sont spécifiés, les enregistrements seront retenus s’ils remplissent toutes les conditions.

Si l'on veut les articles publiés (c'est à dire statut supérieur à zéro) ET du type 'article' :

<LOOP NAME="tous_les_articles_publiés" TABLE="textes" WHERE=”status GT 0" WHERE="type EQ 'article'">
   <DO>
      <br />- [#TITRE], publié le [#DATEPUBLI].
   </DO>
</LOOP>


L’attribut `ORDER` est optionnel et permet de définir dans quel ordre seront affichées les informations.

Cet attribut doit comprendre un nom de champ suivi d’une instruction facultative permettant de choisir si le tri aura lieu dans l’ordre ascendant ou descendant. Par défaut le tri est ASC, c'est à dire ascendant (de A à Z ou du plus ancien au plus récent, du plus petit au plus grand).

* `ORDER="nom ASC"` : tri suivant le champ nom de A à Z ;
* `ORDER="nom"` : équivalent à la ligne ci-dessus ;
* `ORDER="nom DESC"` : tri suivant le champ nom de Z à A ;
* `ORDER="nom" ORDER="prenom"` : tri suivant le champ nom de A à Z, si deux noms sont identiques, alors le champ prenom sera utilisé pour les trier.

On peut ainsi trier des textes par ordre alphabétique à partir de leur titre :

	<LOOP NAME="tous_les_articles_publiés" TABLE="textes" WHERE=”status GT 0" WHERE="type EQ 'article'" ORDER="titre">
	   <DO>
		  <br />- [#TITRE], publié le [#DATEPUBLI].
	   </DO>
	</LOOP>

Si vous voulez que les résultats s'affichent dans l'ordre défini dans l'interface d'édition, vous devez préciser `ORDER="ordre"`. Dans le cas de plusieurs attributs `ORDER`, le tri s’effectuera dans l’ordre naturel : d'abord la première condition de tri, puis la seconde, ainsi de suite.

Voici des articles publiés et triés par date de publication (descendante) et ensuite par titre.

	<LOOP NAME="tous_les_articles_publiés" TABLE="textes" WHERE="status GT 0" WHERE="type EQ 'article'" ORDER="datepubli DESC" ORDER="titre" >
	   <DO>
		  <br />- [#TITRE], publié le [#DATEPUBLI].
	   </DO>
	</LOOP>


L’attribut `LIMIT` est optionnel et peut être utilisé pour limiter le nombre d’enregistrements retournés ou indiquer un décalage. Cet attribut doit être égal à une valeur numérique (limite du nombre d’enregistrements) ou deux valeurs numériques séparées par une virgule (décalage, limite du nombre d’enregistrements).

* `LIMIT="x"` : retourne les x premiers enregistrements ;
* `LIMIT="1"` : retourne le premier enregistrement ;
* `LIMIT="x,y"` : retourne les enregistrements du (x+1)ième au (x+y)ième, en effet, le premier enregistrement n'est pas le numéro 1, mais 0 ;
* `LIMIT="0,y"` : équivalent à LIMIT="y", de 0 à y ;
* `LIMIT="x,-1"` : retourne les enregistrements du (x+1)ième au dernier ;

Note : le décalage du premier enregistrement est 0 (pas 1) ce qui explique le x+1.

Si on souhaite afficher les 10 derniers articles publiés, classés par date descendante :

	<LOOP NAME="10_derniers_articles_publies_par_date" TABLE="textes" WHERE="status GT 0" WHERE="type EQ 'article'" ORDER="datepubli DESC" LIMIT="0,10">
	   <DO>
		  <br />- [#TITRE], publié le [#DATEPUBLI].
	   </DO>
	</LOOP>

### Pagination des résultats : SPLIT
L'attribut `SPLIT` permet d'afficher les résultats d'une boucle sur plusieurs pages. L'affichage des pages de résultats est géré par la macro PRINT_PAGE_SCALE (définie dans share/macros.html) : elle doit être appelée dans l'une des balises `AFTER` ou `BEFORE` de la boucle. Par exemple, pour afficher 10 résultats par page :

	<LOOP NAME="articles_publies_par_date_affiches_par_10" TABLE="textes" WHERE="status GT 0" WHERE="type EQ 'article'" ORDER="datepubli DESC" SPLIT="10">
	   <DO>
		  <br />- [#TITRE], publié le [#DATEPUBLI].
	   </DO>
	   <AFTER>
		  <MACRO NAME="PRINT_PAGE_SCALE"> <!-- Affiche la barre de navigation en dessous des résultats -->
	   </AFTER>
	</LOOP>

N.B : les attributs `LIMIT` et `SPLIT` ne peuvent pas être utilisés simultanément dans une même boucle.


### 2 variables renvoyées par les boucles : COUNT, NBRESULTS
Si vous souhaitez savoir combien de résultats vous allez afficher : les boucles sur base de données définissent systématiquement les deux variables suivantes :

* `[#COUNT]` qui donne le numéro de l'enregistrement ;
* `[#NBRESULTS]` qui donne le nombre d'enregistrements que la boucle va exécuter.

Veuillez consulter la section consacrée aux possibilités d'affichage avancé avec DOFIRST pour pouvoir bien utiliser ces variables.

### Débuggage : SHOWSQL
Si vous voulez voir la requête SQL générée par une boucle (pour débugger notamment), vous pouvez utiliser l'attribut `SHOWSQL` :

	<LOOP NAME="tous_les_textes" TABLE="textes" SHOWSQL="1">
	   <DO>
		  <br />- [#TITRE], publié le [#DATEPUBLI].
	   </DO>
	</LOOP>


### Utilisation de iddocument, idperson et identry dans la clause WHERE

iddocument, idperson et identry et permette d'effectuer des jointures automatiques entre les tables d'entités et les tables d'index ou d'index de personnes.

On peut par exemple lister les entrées d'index de type motsclesfr associées à un texte en utilisant iddocument de la manière suivante :

	<LOOP NAME="get_motsclesfr" SELECT="nom" TABLE="indexes" WHERE="iddocument='[#ID]' AND type='motsclesfr'">
	 <BEFORE><ul></BEFORE>
	 <DO><li>[#NOM]</li></DO>
	 <AFTER></ul></AFTER>
	</LOOP>


De même, on peut récupérer les traducteurs associées à un texte en utilisant iddocument de la manière suivante :

	<LOOP NAME="get_traducteur" SELECT="nomfamille,prenom" TABLE="auteurs" WHERE="iddocument='[#ID]' AND type='traducteur'">
	 <BEFORE><ul></BEFORE>
	 <DO><li>[#NOMFAMILLE], [#PRENOM]</li></DO>
	 <AFTER></ul></AFTER>
	</LOOP>


Depuis le template associé à une entrée d'index (l'id de l'entrée index courante=[#ID]), on peut lister les textes associés à cette entrée en utilisant identry de la manière suivante :

	<LOOP NAME="get_textes" SELECT="titre" TABLE="textes" WHERE="identry='[#ID]'">
	 <BEFORE><ul></BEFORE>
	 <DO><li>[#TITRE]</li></DO>
	 <AFTER></ul></AFTER>
	</LOOP>


Idem depuis le template associé à une personne (l'id de la personne courante=[#ID]) en utilisant idperson  : 

	<LOOP NAME="get_textes" SELECT="titre" TABLE="textes" WHERE="idperson='[#ID]'">
	 <BEFORE><ul></BEFORE>
	 <DO><li>[#TITRE]</li></DO>
	 <AFTER></ul></AFTER>
	</LOOP>


### Commandes avancées : GROUPBY, SELECT, HAVING

Les commandes suivantes sont beaucoup moins utilisées dans le cadre de l'utilisation simple de Lodel.

Les commandes `GROUPBY`, `HAVING` et `SELECT`` permettent d'utiliser des fonctions d'agrégation pour compter ou pour chercher le maximum, le minimum, la moyenne, la somme etc d'un groupe d'enregistrements.

`GROUPBY` forme un « agrégat », c'est à dire qu'il va écraser un ensemble de données, en général une suite de ligne en éliminant certains doublons.

Ainsi, si nous avons les enregistrements suivants :
```
<table>
<tr>
<th>Statut</th>
<th>Icône associée</th>
<th>Définition</th>
</tt>
<tr>
<td>Auteur</td>
<td>Titre</td>
<td>Date de publication</td>
</tr>
<tr>
<td>Robert Louis</td>
<td>L'utilisation des parachutes</td>
<td>12/04/02</td>
</tr>
<tr>
<td>Andrée Louise</td>
<td>La théorie du complot</td>
<td>14/02/03</td>
</tr>
<tr>
<td>Robert Louis</td>
<td>La chute libre</td>
<td>29/07/01</td>
</tr>
</table>
```
Et si nous appelons ces données par la commande :
```
<LOOP NAME="un_article_par_auteur" TABLE="textes" GROUPBY="auteur">
```
L'instruction GROUPBY va identifier qu'il y a 2 enregistrements ayant le même auteur et va les regrouper pour n'en garder qu'un seul :
```
<table>
<tr>
<th>Statut</th>
<th>Icône associée</th>
<th>Définition</th>
</tt>
<tr>
<td>Auteur</td>
<td>Titre</td>
<td>Date de publication</td>
</tr>
<tr>
<td>Robert Louis</td>
<td>L'utilisation des parachutes</td>
<td>12/04/02</td>
</tr>
<tr>
<td>Andrée Louise</td>
<td>La théorie du complot</td>
<td>14/02/03</td>
</tr>
</table>
```

`SELECT` permet de faire des boucles qui contiennent des instructions spécifiques du langage SQL, en particulier les fonctions natives de MySQL, comme `count()` qui retourne non les résultats, mais le nombre de résultats.

Pour savoir combien de textes sont publiés, on peut écrire :
```
	<LOOP NAME="count_documents" TABLE="textes" SELECT="count(*) as total" WHERE="status GT 0">
	   <DO>
		  <p>Il y a actuellement [#TOTAL] documents publiés.</p>
	   </DO>
	</LOOP>
```

`SELECT="count(*) as total"` permet ici de ne pas sélectionner toutes les données des documents, mais de ne donner que leur nombre. La précision `as total` signifie que ce nombre sera attribué à la variable lodelscript `[#TOTAL]` que nous utiliserons ensuite dans le template.

Cet exemple fonctionne, mais cependant, il faut savoir que :

Les boucles sur base de données définissent systématiquement les deux variables suivantes:

* `[#COUNT]` qui donne le numéro de l'enregistrement ;
* `[#NBRESULTATS]` qui donne le nombre d'enregistrements que la boucle va retourner.

Les attributs `DONTSELECT` et `SELECT` permettent de sélectionner ou de-sélectionner les champs transférés de la base de données. Avec `DONTSELECT` on peut donc ne PAS demander certaines données, avec `SELECT` on précise la liste des données que l'on souhaite avoir.

	<LOOP NAME="juste_titre_date" TABLE="textes" SELECT="titre,datepubli">

`SELECT="titre,datepubli"` nous permettra d'afficher les valeurs de `[#TITRE]` et de `[#DATEPUBLI]`, mais le texte des documents ne sera pas donné, la variable `[#TEXTE]` serait donc vide.

Les deux cas les plus fréquents pour utiliser `SELECT` et `DONTSELECT` sont :

* Éviter de faire appel à des variables que vous utilisiez déjà avant une boucle. Par exemple, si la variable [#ID] est définie dans votre page et qu'une boucle pourrait la redéfinir malencontreusement et l'écraser, vous pouvez éviter cela avec : `DONTSELECT="id"`.
* Optimiser les transferts de la base de données. Cependant, des essais ont montré que même le transfert de texte long ne change en rien le temps de création d'une page. Ces commandes ne doivent être utilisées qu'en cas de besoin réel.

La commande `SELECT` combinée à la commande SQL `as` permet aussi de définir un nouveau nom à une variable, ce qui peut être utile si on veut réutiliser une variable dans le cas de boucles imbriquées

	<LOOP NAME="select_as" TABLE="textes" SELECT="id as iddocument">
	   <DO>
		   [#IDDOCUMENT]
	   </DO>
	</LOOP>


### Combinaisons (AND, OR)

Les critères spécifiés grâce à l’attribut WHERE peuvent être très fins grâce à des opérateurs et des fonctions, nous vous recommandons de lire un document traitant de la commande WHERE. Par exemple sur le site de MySQL : <http://www.mysql.com>

Quelques exemples de `WHERE` avec des opérateurs d'addition :

<LOOP NAME="maboucle" TABLE="textes" ORDER="datepubli DESC" WHERE="parent ne 'actualites' AND parent ne 'annuaire' WHERE="status gt 0" LIMIT="0,9">

Cette boucle va sélectionner les 10 derniers documents publiés (ordonnés par date, limités à 10 et statut GT '0') qui ne sont contenus ni dans la rubrique 'actualites', ni dans la rubrique 'annuaire'. Grâce à `AND`, vous pouvez donc combiner des conditions.

`OR` permet de grouper des conditions avec une alternative :
```
<LOOP NAME="maboucle" TABLE="textes" ORDER="datepubli DESC" WHERE="parent ne 'actualites' OR parent ne 'annuaire' WHERE="statut gt 0" LIMIT="0,10">
```

On obtient dans ce cas, les documents qui appartiennent soit à la rubrique actualités, soit à la rubrique annuaire.

On peut regrouper les conditions dans des parenthèses.

Quelques pointeurs pour aller plus loin sur les fonctions :

* (NOT) LIKE, SUBSTRING : <http://dev.mysql.com/doc/refman/5.0/fr/string-functions.html>
* (NOT) IN, (NOT) BETWEEN : <http://dev.mysql.com/doc/refman/5.0/fr/comparison-operators.html>
* AND, OR : <http://dev.mysql.com/doc/refman/5.0/fr/logical-operators.html>

## Possibilités d'affichage évoluées dans les boucles

Il est possible de définir dans une boucle du code à exécuter suivant certains cas, comme par exemple pour le premier enregistrement ou lorsqu’il n’y a pas de résultats retournés. Pour pouvoir utiliser ces fonctionnalités, la boucle doit être définie avec des balises supplémentaires comme ci-dessous :
```
	<LOOP NAME="ma_boucle" TABLE="table1" TABLE="table2" WHERE="critere1" ORDER="ordre1">
	   <BEFORE>
		  code exécuté avant l’affichage des enregistrements
	   </BEFORE>
	   <DOFIRST>
		  code exécuté pour le premier enregistrement et seulement pour lui
	   </DOFIRST>
	   <DO>
		  code exécuté pour tous les autres enregistrements (sauf le premier si DOFIRST est défini et sauf le dernier si DOLAST est défini)
	   </DO>
	   <DOLAST>
		  code exécuté pour le dernier enregistrement (sauf si c’est aussi le premier)
	   </DOLAST>
	   <AFTER>
		  code exécuté après l’affichage des enregistrements
	   </AFTER>
	   <ALTERNATIVE>
		  code exécuté si aucun enregistrement n’est trouvé
	   </ALTERNATIVE>
	</LOOP>
```

Note : ces balises supplémentaires peuvent être utilisées indépendamment les unes des autres.

### Alternative

La balise `<ALTERNATIVE>` permet de spécifier le code qui sera exécuté s’il n’y aucun enregistrement trouvé. Cette balise ne fonctionne que pour les boucles sur les bases de données (c'est à dire ne fonctionne pas pour les boucles de type prédéfini).

Exemple, en considérant que la table textes ne contient pas d'article :

**template** :

	<h1>Liste des articles</h1>
	<LOOP NAME="liste_articles" TABLE="textes" WHERE="type='article'" ORDER="titre">
	   <DO>
		  <a href="affiche_article.php?id=[#ID]">[#TITRE]</a><br />
	   </DO>

	   <ALTERNATIVE>
		  Aucun article trouvé.
	   </ALTERNATIVE>
	</LOOP>


**résultat** :

	<h1>Liste des articles</h1>
	Aucun article trouvé.


### Dofirst & Dolast

Permettent de spécifier un code particulier pour les premier et dernier enregistrements. Ces balises ne fonctionnent que pour les boucles base de données (c'est à dire ne fonctionne pas pour les boucles de type prédéfini).

Exemple :

**template** :

	<p>Document écrit par :
	<LOOP NAME="liste_auteur" TABLE="auteurs" ORDER="nom" ORDER="prenom">
	   <DOFIRST>
		  [#PRENOM] [#NOM]
	   </DOFIRST>

	   <DO>
		  , [#PRENOM] [#NOM]
	   </DO>

	   <DOLAST>
		  et [#PRENOM] [#NOM].
	   </DOLAST>
	</LOOP>
	</p>


**résultat** :

	<p>Document écrit par : Ghislain Picard, François Lermigeaux et Gautier Poupeau.</p>


### Before & After

Permettent de spécifier du code qui sera exécuté avant le premier enregistrement ou après le dernier enregistrement. Ces balises fonctionnent avec les boucles de base de données et les boucles prédéfinies uniquement si le code de la fonction PHP le prévoit, ce qui est généralement le cas.

Une utilisation fréquente est la création d’un tableau avec des lignes de titre uniquement s'il y a des résultats à afficher :

Exemple :

**template** :

	<LOOP NAME="liste_auteur" TABLE="auteurs" ORDER="nom" ORDER="prenom">
	   <BEFORE>
		  <table>
			  <th>
				 <td>Prénom</td>
				 <td>Nom</td>
			  </th>
	   </BEFORE>
	   <DO>
		  <tr>
			 <td>[#PRENOM]</td>
			 <td>[#NOM]</td>
		  </tr>
	   </DO>
	   <AFTER>
		  </table>
	   </AFTER>
	   <ALTERNATIVE>
	   Aucun auteur trouvé.
	   </ALTERNATIVE>
	</LOOP>

**résultat s’il y a des enregistrements :**

	<table>
	   <th>
		  <td>Prénom</td>
		  <td>Nom</td>
	   </th>
	   <tr>
		  <td>Antoine</td>
		  <td>de Saint Exupery</td>
	   </tr>
	   <tr>
		  <td>Paul</td>
		  <td>Verlaine</td>
	   </tr>
	   <tr>
		  <td>Jules</td>
		  <td>Verne</td>
	   </tr>
	</table>

**résultat s’il n’y a pas d’enregistrements :**

	Aucun auteur trouvé.
	
## Boucles prédéfinies 


Pour effectuer une boucle prédéfinie il faut utiliser la syntaxe suivante :

	<LOOP NAME="nom_fonction">
	   <DO>
		  code de la boucle
	   </DO>
	</LOOP>


Cette boucle va appeler la fonction PHP prédéfinie correspondant au nom « nom_fonction ». Cette fonction va remplir certaines variables qui seront accessibles dans le code de la boucle.

Ces boucles sont codées en PHP et dépendent donc du contexte dans lequel vous utilisez lodelscript. Lodel comporte certaines boucles prédéfinies, sur lesquelles nous allons nous appuyer, mais vous pouvez très bien en coder de nouvelles. Voir le fichier boucles.php dans les sources de Lodel pour ajouter des boucles personnalisées.

### La boucle TOC

Cette fonction permet de générer la table des matières d’un document, celui-ci doit avoir été convenablement stylé dans votre traitement de texte avec l'utilisation des styles titre1, 2, 3 etc.

Pour appeler cette fonction, vous devrez ajouter dans votre template cette boucle :

	<LOOP NAME="toc" TEXT=”texte”>
	   <IF COND="[#NIVEAU]==1">
		  <a href="#tocto[#TOCID]"NAME="tocfrom[#TOCID]">
			 [#TITRE]
		  </a>
	   </IF>
	</LOOP>


Cette boucle permet d’afficher tous les titres de premier niveau contenu dans le texte de votre document, si vous voulez aussi ajouter les titres de second niveau, vous devrez ajouter à l’intérieur de votre boucle :

	<IF COND="[#NIVEAU] EQ '2' "></IF>

et ainsi de suite pour les autres niveaux.

L’attribut TEXT à l’intérieur du `<LOOP>` permet de déterminer quelle partie de votre document la TOC doit prendre en compte. Si vous voulez prendre en compte le texte et les annexes, vous noterez `TEXT= "texte, annexe”` et juste les annexes `TEXT="annexe”` … etc.

Si vous voulez que chaque titre à l’intérieur de votre texte soit un lien qui renvoie à la table des matières, vous devrez rajouter la fonction filtre (pipe) 'tocable' à la variable [#TEXTE] :

	[(#TEXTE|tocable)]

Voir la section consacrée aux filtres pour cela.

### Les liens PREVIOUS / NEXT

Les boucles PREVIOUS et NEXT permettent de faire dynamiquement des liens d'une entité vers les entités suivantes et précédentes.

On les appelle avec ID correspondant à l'ID du document ou de la publication en cours.

Exemples :

	 <LOOP NAME="previous" ID="[#ID]">

	 <LOOP NAME="next" ID="[#ID]">

THROUGH est facultatif. Il permet de traverser un niveau de publication (dont le/les types sont donnés par THROUGH). Cela est très utile, en particulier si vous souhaitez que les liens « traversent » des regroupements, des rubriques ou des numéros.

	<LOOP NAME="previous" ID="[#ID]" THROUGH="rubrique">
	   <DO>
		  <a href=''document.html?id=[#ID]''>Suivant</a>
	   </DO>
	</LOOP>


Il est possible de spécifier plusieurs types :

 <LOOP NAME="previous" ID="[#ID]" THROUGH="rubrique,numero">


La boucle exporte toutes les variables de la table entités : `[#ID]`, `[#IDPARENT]`, `[#STATUT]`... ainsi que le nom du type de l'entité : `[#TYPE]`.

### Les listes suivants / précédents

Dans une boucle, quelle qu’elle soit, il est très facile de construire des liens « suivants » et « précédents » pour naviguer dans des listes de résultats, par exemple de 10 en 10.

Pour déclencher ce comportement, il suffit d’indiquer dans l’attribut LIMIT un nombre représentant la quantité d’éléments souhaités, lodel fabrique alors le nombre de pages nécessaire et propose des liens sous la forme des variables `[#NEXTURL]` et `[#PREVIOUSURL]`.

Voici un exemple qui liste les titres de tous les documents, de 20 en 20 en les classant par date de publication.

	<LOOP NAME="touslesdocuments" TABLE="documents" ORDER="datepubli DESC" LIMIT="20">
	   <DO>
		  <li>[#TITRE]</li>
	   </DO>
	   <AFTER>
		  <IF COND="[#NEXTURL]"><a href="[#NEXTURL]">Suivants</a></IF>
		  <IF COND="[#PREVIOUSURL]"><a href="[#PREVIOUSURL]">Précédents</a></IF>
	   </AFTER>
	</LOOP>


Les variables `[#NEXTURL]` et `[#PREVOUSURL]` pointent directement vers la bonne page. Les tests ci-dessus permettent de n'afficher les liens que s'ils restent des résultats.

### La boucle EXTRAIT_IMAGES

Cette boucle va chercher à l'intérieur d'un document les images qui y sont contenues pour les rendre disponibles. Vous pouvez alors afficher une image tirée d'un document sans pour autant l'afficher complètement.

	<LOOP NAME="EXTRAIT_IMAGES" TEXT="[#TEXTE]">
	   [#IMAGE]
	</LOOP>


Cet boucle va alors afficher toutes les images. Si on souhaite limiter, il faut utiliser la commande LIMIT, comme suit pour la première image :

	<LOOP NAME="EXTRAIT_IMAGES" TEXT="[#TEXTE]" LIMIT="0,1">
	   [#IMAGE]
	</LOOP>


La variable `[#IMAGE]` contient tout le tag HTML : `<img src=''chemin/vers/image.gif''>`, si on ne souhaite que le chemin pour personnaliser le tag `<img>`, il faut écrire `[#SRC]` :

	<LOOP NAME="EXTRAIT_IMAGES" TEXT="[#TEXTE]" LIMIT="1">
	   <img src="[#SRC]" alt="mon image">
	</LOOP>


Variables disponibles : "src","alt","border","style","class","name".

### La boucle PARAGRAPHES

Elle permet de parcourir les paragraphes d'un texte les uns après les autres.

Elle demande un argument TEXT, qui sera le texte parcouru par la boucle. Les paragraphes sont affichables les un après les autres par la variable [#PARAGRAPHE] et une variable [#COMPTEUR] est incrémentée automatiquement.

	<LOOP NAME="PARAGRAPHES" TEXT="[#TEXTE]">
	   <p>Paragraphe numéro [#COMPTEUR] : [#PARAGRAPHE]</p>
	</LOOP>


### La boucle RSS

Elle permet à Lodel de lire un flux RSS, c'est à dire un fil de syndication, proposé par un autre site que le vôtre. Il suffit de la mettre en place dans vos templates pour que vous puissez afficher des informations proposées par d'autres sites.

La boucle générale s'appelle avec le nom rss, elle correspond à l'ensemble du fil RSS, avec les variables générales du fil. Ensuite, chaque article du fil est accessible par la boucle "rssitem".

	<LOOP NAME="rss" URL="[#URL]" REFRESH="600">
	   <h2>[#TITLE]</h2>
	   <ul>
		  <LOOP NAME="rssitem" LIMIT="0,10">
			 <li><a href="[#LINK]">[#TITLE]</a>
				<IF COND="[#AUTHOR]">par [#AUTHOR]</IF>
				<IF COND="[#CATEGORY]"> dans [#CATEGORY]</IF>
				<br/>[#DESCRIPTION]
			 </li>
		  </LOOP>
	   </ul>
	</LOOP>


# Modification des variables : fonctions filtres ou pipes

Il est possible d’appliquer des fonctions aux variables pour les modifier au moment de l'affichage. Cela est particulièrement utile pour conserver des informations dans la base de données tout en les adaptant à votre mise en page : mise en majuscules, raccourcir un texte long, enlever des mises en forme, etc.

Pour appliquer une fonction à une variable, il faut faire suivre la variable du caractère |("pipe" en anglais) puis du nom de la fonction.

	[#VARIABLE|fonction]

Certaines fonctions peuvent accepter des paramètres qui sont passés entre parenthèses, séparés par des virgules, après le nom de la fonction.

	[#VARIABLE|fonction(param1, param2)]

Ces fonctions sont écrites en PHP et dépendent donc du contexte dans lequel vous utilisez Lodelscript. Lodel comporte certains filtres prédéfinis, stockés dans le fichier <nowiki>lodel/scripts/textfunc.php</nowiki>. Si vous souhaitez ajouter des filtres personnalisés dans les sources de Lodel, créez le fichier <nowiki>lodel/scripts/textfunc_local.php</nowiki>, et insérez vos filtres dans ce fichier.
  
## wiki
  
Si vous souhaitez permettre à vos utilisateurs d’utiliser la syntaxe wiki dans leurs formulaires vous disposer du filtre `|wiki`.

Données entrées dans la variable `[#NOTES]`:

	Voici mes mots en ''italiques'' et aussi en __gras__;

**template** :

	<p>[#NOTES|wiki] </p>


**résultat** :

	<p> Voici mes mots en italiques et aussi en gras.</p>


## tocss

Le filtre 'tocss' (lire "to css") effectue les nettoyages et les transformations pour traduire les styles importés par le traitement de texte en balises HTML.

Elle donne alors des classes du type :

	<div class="nom_du_style">texte du div.</div>

Cette fonction est importante et doit être appliquée à tous les champs qui comportent plus d'un paragraphe importés par l'intermédiaire de servOO ou OTX.

Par défaut, les niveaux de titre sont codés `<div class="sectionx">` où x est le niveau du titre. En ajoutant le paramètre heading : `[#VAR|tocss('heading')]` au filtre tocss, les niveaux de titre sont codés `<hx>` comme recommandé en XHTML.

## lettrine

Permet d’extraire la première lettre d’un texte contenu dans une variable avant de l'afficher avec un style particulier.

**variables** :

	[#TEXTE] :
	<p>Les sanglots longs des violons de l'automne, blessent mon coeur d'une langueur monotone</p>


**template** :

	[#TEXTE|lettrine]

**résultat** :

	<p><span class="lettrine">L</span>es sanglots longs des violons de l'automne, blessent mon coeur d'une langueur monotone</p>

## multiline

Permet de passer à la ligne tout les x caractères sans couper les mots sauf si un mot fait plus de x caractères. Le nombre de caractères par lignes doit être passé en variable. Cette fonction est très utile pour les balises <textarea> afin d’éviter d’avoir un ascenseur horizontal.

Note : le comportement par défaut des navigateurs ne nécessite plus l’utilisation de cette fonction.

**variables** :

	#TEXT :
	Les sanglots longs des violons de l'automne, blessent mon coeur d'une langueur monotone


**template** :

	<form>
	   <textarea cols="20" rows="10">[#TEXT|multiline(20)]</textarea>
	</form>


**résultat** :

	<form>
	   <textarea>Les sanglots longs
	des violons de
	l'automne, blessent
	mon coeur d'une
	langueur monotone
	</textarea>
	</form>


## nbsp

Cette fonction renvoie un espace insécable si la variable est vide. Cela permet d'éviter les cases vides dans les tables.

Si par exemple on a un titre, mais parfois pas de sous-titre dans un tableau, on peut remplir les cases vides par des `&nbsp;`

**template** :

	<LOOP NAME=''nbsp'' TABLE=''documents'' WHERE=''type EQ 'article**>
	   <tr><td>[#TITRE]</td><td>[#SOUSTITRE]</td></tr>
	</LOOP>


**résultat** :

	<tr><td>Rapport général</td><td>pour l'année 2002</td></tr>
	<tr><td>Comptes</td><td>&nbsp;</td></tr>
	<tr><td>Bilan annuel</td><td>de l'association lodel</td></tr>


## strtoupper, strtolower

Passe toutes les lettres de la variable en majuscules et minuscules respectivement.

**variables** :

	#TEXTE :
	C’est la rentrée, les élèves sont en classe.


**template** :

	Le texte brut : [#TEXTE]<br />
	Le texte modifié : [#TEXTE|strtoupper]<br />


**résultat** :

	Le texte brut : C’est la rentrée, les élèves sont en classe.<br />
	Le texte modifié : C'EST LA RENTRÉE, LES ÉLÈVES SONT EN CLASSE.<br />


## majuscule
Met en majuscule la première lettre du texte.

**variables** :

	#TEXTE :
	c’est la rentrée, les élèves sont en classe.


**template** :

	Le texte modifié : [#TEXTE|majuscule]<br />


**résultat** :

	Le texte modifié : C’est la rentrée, les élèves sont en classe.<br />


## textebrut

Cette fonction transforme la variable en supprimant toutes les balises HTML et en remplaçant les espaces insécables, les tabulations et les retours à la ligne par des espaces.

**variables** :

	#TEXTE :
	<p>Les sanglots longs des violons de l'<strong>automne</strong>,nblessent mon coeur d'une langueur monotone</p><p>Paul&nbsp;Verlaine</p>

**template** :

	Le texte : [#TEXTE]<br />
	Le texte modifié : [#TEXTE|textebrut]<br />


**résultat** :

	Le texte brut : <p>Les sanglots longs des violons de l'<strong>automne</strong>,

	blessent mon coeur d'une langueur monotone</p><p>Paul&nbsp;Verlaine</p><br />

	Le texte modifié : Les sanglots longs des violons de l'automne, blessent mon coeur d'une langueur monotone Paul Verlaine<br />

Ce filtre est utile pour le <TITLE> d'une page HTML par exemple. Attention toutefois avec les écritures non latines, l'affichage du titre dans la barre d'état du logiciel peut être incorrecte dans les navigateurs actuels.


## cuttext

Équivalent de la fonction couper en Lodelscript 0.7. 
Affiche les n premiers caractères d’une variable et ajoute la chaîne « … » à la fin de l’extrait. Le nombre de caractères est passé à la fonction. Cette fonction est utile pour afficher le début d’un article sur une page d’accueil par exemple.

Cette fonction gère automatiquement les balises HTML qui se trouveraient dans votre texte. Ainsi, si une balise s'ouvrait avant la coupure, elle sera automatiquement refermée. Cela évite de laisser une balise ouverte qui s'appliquerait à tout le reste de votre page.

**arguments de la fonction cuttext** :
* 1er argument : length = (int, default=100) nombre de caractère conservé
* 2e argument  : dots = (bool, default=false) affichage de la chaîne « … » à la fin de l’extrait
* 3e argument  : html = (bool, default=true) conserve la structuration html 

**variables** :

	#TEXTE :
	Les sanglots longs des violons de l'automne, blessent mon coeur d'une langueur monotone


**template** :

	Le texte : [#TEXTE]<br />
	Le texte modifié : [#TEXTE|cuttext(40,true)]<br />


**résultat** :

	Le texte brut : Les sanglots longs des violons de l'automne,

	blessent mon coeur d'une langueur monotone<br />

	Le texte modifié : Les sanglots longs des violons de ...<br />


## couperpara

Cette fonction permet de n’afficher que les n premiers paragraphes d’une variable.

**variables** :

	#TEXTE :
	<p>Premier paragraphe</p>
	<p>Deuxième paragraphe</p>
	<p>Dernier paragraphe</p>


**template** :

	Le texte brut : <br />
	[#TEXTE]
	Le texte modifié : <br />
	[#TEXTE|couperpara(2)]


**résultat** :

	Le texte brut :
	<p>Premier paragraphe</p>
	<p>Deuxième paragraphe</p>
	<p>Dernier paragraphe</p>
	Le texte modifié :
	<p>Premier paragraphe</p>
	<p>Deuxième paragraphe</p>


## humandate

Permet d’afficher une date dans un format du type 01 janvier 2003. Si l’année est supérieure à 9000, la fonction renvoie « jamais » et si l’année est nulle la fonction n’affiche rien.

**variables** :

	#DATE :
	1981-07-31


**template** :

	Le texte a été écrit le [#DATE|humandate].


**résultat** :

	Le texte a été écrit le 31 juillet 1981.


## formateddate, formatedtime

Les fonctions formattedate et formatedtime permettent de formater respectivement une date ou un « timestamp ». Le format de sortie est à préciser ainsi :

	[#DATEPUBLI|formateddate("%A %d %B %Y")]

Donnera « Mercredi 31 mars 2004 », en effet '%A' signifie « jour de la semaine », '%d' numéro du mois et ainsi de suite. Référence complète des codes de formatage : <http://fr2.php.net/manual/fr/function.strftime.php>

## tocable

Permet de rendre rétrocliquable les titres. S'utilise avec la boucle prédéfinies TOC (voir supra).

## vignette

Cette fonction permet d’afficher la miniature d’une image dont l’url est contenue dans la variable. L’url de l’image est remplacée par celle de la miniature. La largeur de la vignette doit être passée en paramètre de la fonction.

Si l’image miniature n’existe pas, elle sera créée et stockée automatiquement. L’url peut être absolue ou relative.

**variables** :

	#IMG :
	http://www.revues.org/commun/logos/300X61.jpg


**template** :

	L’image normale: <img src="[#SRC]" /><br />
	La vignette de largeur 100 pixels : <img src="[#SRC|vignette(100)]" /><br />


**résultat** :

	L’image normale: <img src="http://www.revues.org/commun/logos/300X61.jpg" /><br />
	La vignette de largeur 100 pixels : <img src="http://www.revues.org/commun/logos/300X61-small100.jpg" /><br />


Note : cette fonction nécessite l’installation de la librairie GD 2.0.1 et du module GD de php. Ce module est courant chez la majorité des hébergeurs. Au besoin vous pouvez le vérifier en utilisant la fonction phpinfo() sur une de vos pages.



## removefootnotes, removeennotes et removenotes

Supprime les renvois vers les notes de bas de page, les fins de notes et toutes les notes respectivement.

## isadate

Cette fonction renvoie vraie si la variable n’est pas une date vide. On l'utilise donc dans des tests :

	<IF COND=''[#DATEPUBLI|isadate]''>c'est bien une date !<ELSE>Ce n'est pas une date…</IF>

## replacequotationmark

Permet de remplacer les guillemets contenus dans la variable par l’entité html correspondante (&quot;)

**variables** :

	#TEXTE :
	"Les sanglots longs des violons de l'automne, blessent mon coeur d'une langueur monotone"


**template** :

	Le texte : [#TEXTE]<br />
	Le texte modifié : [#TEXTE|replacequotationmark]<br />


**résultat** :

	Le texte brut : "Les sanglots longs des violons de l'automne,
	blessent mon coeur d'une langueur monotone"<br />
	Le texte modifié : &quot;Les sanglots longs des violons de l'automne,
	blessent mon coeur d'une langueur monotone&quot;<br />



## Filtres pour les champs multi-langues

	[#RESUME|multilingue("fr")] est équivalent à [#RESUME:FR].

Ce filtre peut néanmoins être intéressant dans le cas de filtrages automatisés.

	[#RESUME|humanlang] : renvoie la langue de la variable sous sa forme lisible « français » et non fr par exemple.

## replace

Identique à la fonction PHP str_replace :

**variables** : 
	[#TEXTE]
	"Ce document est en français !"

**template** :

	[#TEXTE|replace('français', 'anglais')]


**résultat** : 
	"Ce document est en anglais !"

## reg_replace

Identique à la fonction PHP preg_replace.

**variables** : 

	[#TEXTE]
	"Ce document est pour Lodel 0.8 !"

**template** :

	[#TEXTE|reg_replace('/Lodel \d\.\d/', 'Lodel dans sa version actuelle')]

**résultat** : 

	"Ce document est pour Lodel dans sa version actuelle !"

## today et today_with_hour

Retournent la date du jour avec ou sans l'heure

## hideifearlier

Retourne le texte si la date est dépassée, sinon retourne une chaine vide

## imagewidth et imageheight

Retournent la largeur ou la hauteur d'une image

## nicefilesize

Renvoie la taille d'un fichier, mais formate joliment avec des kilos et mégas

## paranumber

Numerotation des paragraphes : ajoute un <nowiki><span class="paranumber"></nowiki> contenant une ancre avec le numero du paragraphe aux paragraphes ayant le style texte par défaut. Les paramètres sont modifiables dans le template et écrasent les paramètres par défaut.

## formatstring

Affiche l'argument selon le format (utilise la fonction PHP sprintf)

## ishtml

Retourne true si le texte comporte des balises HTML

## defaultvalue

Retourne la valeur du paramètre si la variable est vide ou null

## removeimages

Supprime les images contenues dans le texte

## removetags

Supprime les balises HTML spécifiés passés en paramètres

## removelinks

Supprime les liens contenus dans le texte

## getFileType

Renvoie le type seul d'un fichier (UNIX-Like uniquement)

## mysql2TS

Transforme une date MySql en timestamp UNIX 

## time2Date

Transforme un timestamp MySql en date (format anglais) 

## date2Time

Transforme un timestamp MySql en date MySql 

## LSgmstrftime

Formate une date/heure GMT/CUT en fonction de la configuration locale (pour LS) 

## formatIdentifier

Création d'un identifier à partir d'une chaine de caractères

## cleanBadChars

Nettoyage des caractères windows illegaux + nettoyage pour flux XML

## HTML2XML

Conversion entités html en entités xml 

## getParentByType

récupère l'ID du parent d'une entité en fonction de son type

## cryptEmails

Crypte les emails pour qu'ils ne soient pas reconnaissable par les robots spam. Ce filtre ajoute dans la source HTML des spans cachés dans le contenu du lien, supprime le contenu du href du lien. Lors du clic sur le lien par l'utilisateur, du code JavaScript recompose le <nowiki>mailto:</nowiki>.

## cleanCallNotes

Nettoie les mises en forme locales sur les appels de notes

## highlight_code

Coloration syntaxique de code (HTML et XML)

## lexplode

Wrapper de la fonction PHP 'explode'

## Fonctions diverses (réservées à l'interface de lodel)

Voici la liste de fonctions existantes, mais conçues pour l'interface de Lodel.
* function yes : renvoie "checked" si vrai
* function no : renvoie "checked" si faux
* function eq(str) : renvoie "checked" si égale à 'str'
* function notes(type) : fonction pour sélectionner dans les footnotes ou les endnotes un seul type de notes : type=nombre, lettre ou astérisque.
* function isrelative : permet de savoir si un lien est relatif
* function isabsolute : permet de savoir si un lien est absolu
* function strip_tags_keepnotes(keeptags) Enleve les tags HTML qui gardent les footnotes et les endnotes de OpenOffice

## Filtres PHP et développements

Les fonctions php qui modifient les chaînes de caractères peuvent être utilisées directement comme des filtres lodelscript.

Exemple : la fonction php trim() enlève les espaces en début et en fin de chaîne. On peut donc effectuer ce nettoyage en écrivant :

	[#TITRE|trim]

Consultez la liste des fonctions sur les chaînes de caractères dans la documentation de Php : <http://www.php.net/manual/fr/ref.strings.php>

Vous pouvez développer vos propres filtres. Pour cela consultez les sources de Lodel et le fichier textfunc.php.

## Combinaisons de modificateurs de variables

Il est possible d’appliquer plusieurs fonctions à une variable. Il suffit de mettre bout à bout les noms des fonctions séparés par le caractères ‘|’ (pipe). Les fonctions seront exécutées de gauche à droite. Attention, l'ordre des filtres a une incidence sur le résultat. Il est donc important de réfléchir à l'ordre d'exécution des filtres.

**variables** :

	#TEXTE :
	"Les sanglots longs des violons de l'automne, blessent mon coeur d'une langueur monotone"


**template** :

	Le texte modifié : [#TEXTE|replacequotationmark|majuscules]<br />


**résultat** :

	&quot;LES SANGLOTS LONGS DES VIOLONS DE L'AUTOMNE, BLESSENT MON COEUR D'UNE LANGUEUR MONOTONE&quot;<br />


# Macros et fonctions
## Macros
Les macros sont des extraits de template qui sont utilisés plusieurs fois dans un template ou dans plusieurs templates déférents. Les macros peuvent être définies et regroupées dans des fichiers qu’il faut inclure dans le fichier template grâce à l’instruction suivante :

	<USE MACROFILE="macro.html">

Après cette instruction, toutes les macros définies dans le fichier macro.html seront accessibles dans le fichier template.

La définition d’une macro se fait comme suit :

	<DEFMACRO NAME="nom_de_la_macro">
	   corps de la macro
	</DEFMACRO>


Le nom de la macro peut être composé de lettres majuscules et minuscules, de chiffres et du caractère ‘_’. Les lettres accentuées, le point et le tiret sont interdits.

Pour appeler une macro il faut utiliser la commande ci-dessous :

	<MACRO NAME="nom_de_la_macro" />

Exemple :

**Fichier macro.html :**

	<DEFMACRO NAME="exemple">
	   <strong>Ceci est un exemple.</strong>
	</DEFMACRO>


**Fichier template :**

	<USE MACROFILE="macro.html" />
	<h1>Exemple de macro</h1>
	Premier appel :<br />
	<MACRO NAME="exemple" />
	<br />
	Deuxième appel :<br />
	<MACRO NAME="exemple" />
	<br />
	Dernier appel :<br />


**résultat** :

	<h1>Exemple de macro</h1>

	Premier appel :<br />
	<strong>Ceci est un exemple.</strong>
	<br />
	Deuxième appel :<br />
	<strong>Ceci est un exemple.</strong>
	<br />
	Dernier appel :<br />
	<strong>Ceci est un exemple.</strong>
	<br />


## Fonctions
Il est aussi possible de définir en Lodelscript des fonctions, avec la balise <DEFFUNC>. La définition des arguments se fait avec les attributs REQUIRED, pour les arguments obligatoires, et OPTIONAL pour les arguments optionnels. Il est possible de ne mettre que des arguments optionnels, ou que des arguments obligatoires.<br />
N.B : les variables définies à l'intérieur d'une fonction ne sont pas accessibles à l'extérieur de la fonction.

La définition d’une fonction se fait comme suit :

	<DEFFUNC NAME="nom_de_la_fonction" REQUIRED="argument_1,argument_n" OPTIONAL="argument_1,argument_n">
	   corps de la fonction
	</DEFFUNC>


Le nom d'une fonction peut être composé de lettres majuscules et minuscules, de chiffres et du caractère ‘_’. Les lettres accentuées, le point et le tiret sont interdits.

Pour appeler une fonction il faut utiliser la commande ci-dessous :

	<FUNC NAME="nom_de_la_fonction" NOM_ARGUMENT_1="valeur" NOM_ARGUMENT_n="valeur" />

Par exemple, pour définir une fonction avec 2 arguments obligatoires et un argument optionnel :

**Fichier macro.html :**

	<DEFUNC NAME="exemple" REQUIRED="COLOR,SIZE" OPTIONAL="BORDER">
	   <p>La couleur est [#COLOR].</p>
	   <IF COND="[#BORDER]">
		  <p>La bordure est de [#BORDER].</p>
	   </IF>
	</DEFUNC>


**Fichier template** :

	<USE MACROFILE="macro.html" />
	<h1>Exemple de fonction</h1>
	<h2>Premier appel : valeur de l'attribut optionnel non définie</h2>
	<FUNC NAME="exemple" COLOR="ffffff" SIZE="10">
	<h2>Deuxième appel : valeur de l'attribut optionnel définie</h2>
	<FUNC NAME="exemple" COLOR="#000000" SIZE="10" BORDER="0">


**résultat** :

	<h1>Exemple de fonction</h1>
	<h2>Premier appel : valeur de l'attribut optionnel non définie</h2>
	<p>La couleur est #ffffff.</p>
	<h2>Deuxième appel : valeur de l'attribut optionnel définie</h2>
	<p>La couleur est #000000.</p>
	<p>La bordure est de 0.</p>


## Inclusion de fichiers template

Il est possible d’inclure un fichier template dans un autre fichier template lorsqu’ils sont situés dans le même répertoire tpl. La syntaxe est la suivante :

	<USE TEMPLATEFILE="fichier">

# Intégrer PHP à Lodelscript
## PHP dans lodelscript

Il est possible d'intégrer du code PHP à du code lodelscript. Pour cela, il suffit d'utiliser les balises d'ouverture et de fermeture de php : <?php et ?>

	<DEFMACRO NAME='phpinfo''>
	   <?php phpinfo(); ?>
	</DEFMACRO>


Attention cependant, ce code ne sera exécuté que lorsque les templates seront compilés. Ensuite, le résultat sera mis en cache.

## La gestion du cache : BLOCK, ESCAPE et REFRESH

On peut vouloir que ce code ne soit pas exécuté ni mis en cache, mais obligatoirement exécuté au moment où l'internaute demande la page.

Ce serait le cas si l'on souhaite afficher l'heure ou la date du jour. Pour cela il faut utiliser les balises <ESCAPE>

	<ESCAPE>
	   <?php date("d/m/y");?>
	</ESCAPE>


ESCAPE permet donc d'exécuter systématiquement une partie de code. ESCAPE ne peut contenir que du code php ou du texte html, pas de LodelScript.

Cependant, si l'on souhaite plutôt une mise à jour régulière et non systématique, alors il faut utiliser l'attribut REFRESH qui permet un contrôle poussé de la mise en cache.

L'attribut REFRESH est indiqué en tête de votre **template** :

	<CONTENT VERSION="1.0" LANG="fr" CHARSET="iso-8859-1" REFRESH="3600" />

`REFRESH` supporte deux syntaxes :

Si l'attribut est un nombre, il indique l'intervalle minimal en seconde pour un nouveau calcul de la page : avec `REFRESH="3600"`, le fichier est recalculé si la version dans le cache a été produite il y a plus d'une heure ET si la page est demandée. La page n'est donc PAS recalculée toutes les heures automatiquement.

Si l'attribut est de la forme hh:mm ou hh:mm:ss, alors le fichier est recalculé une fois passée l'heure indiquée.

Cela est utile quand on sait qu'une information arrive a telle ou telle heure et qu'on souhaite mettre immédiatement le site à jour (c'est le cas pour les flux RSS ou ATOM). Ce contrôle peut aussi être utile lorsque l'on gère un calendrier, un `REFRESH="0:00"` met le site à jour.

Il est possible d'utiliser plusieurs heures, dans la balise :

`REFRESH="6:00, 12:00, 18:00"` les espaces ne sont pas significatifs.

Depuis Lodel 0.9, il est possible de découper un template par bloc, ceux-ci ayant leur propre charset ainsi que refresh. Pour celà, il faut utiliser la balise `<BLOCK>`. Cette balise doit obligatoirement avoir un identifiant numérique unique.

	 <BLOCK ID="1" REFRESH="600" CHARSET="utf-8">
	   Ceci est un bloc qui sera rafraichit toutes les 600 secondes indépendamment du template, et est encodé en UTF-8.
	 </BLOCK>

# Jeu de caractères

Lodel produit par défaut des caractères en UTF-8 ce qui permet de supporter d'afficher des caractères spéciaux mais aussi de gérer les alphabets non latins.

Cependant, comme peu d'éditeurs HTML supporte l'édition en UTF-8, il est possible d'écrire les templates en ISO-8859. Pour cela, il faut definir au début du **template** :

	<CONTENT VERSION="1.0" LANG="fr" CHARSET="iso-8859-1"/>

Votre template sera ensuite traduit automatiquement en UTF-8 par Lodel.

Les attributs `VERSION` et `LANG` ne sont pas utilisées actuellement mais devrait l'être. Il donne de toute façon une information utile.

# Multilinguisme

Les éléments qui permettent la gestion du multilinguisme dans Lodel sont les suivants :

1.  les champs multilingues (de type MLTEXT ou MLLONGTEXT) définis dans les entités (par exemple le champ RESUME dans la classe d'entité "textes"). Ce "champ" accepte un contenu dans plusieurs langues (dans la page d'édition de l'entité, Lodel propose un menu déroulant "ajouter" avec la liste des langues déclarées dans la configuration). On peut donc ajouter un résumé en français, anglais, espagnol...
Pour afficher ce type de champ dans la maquette du site, il faut utiliser la syntaxe suivante dans les templates :
`[#RESUME:FR]` ou `[#RESUME:EN]`, etc.
Pour récupérer toutes les langues utilisées pour un champ multilingue donné, il est possible d'utiliser un [`<IF>` avec une expression régulières](#conditions-utilisant-les-expressions-r%C3%A9guli%C3%A8res). 

2.  les variables de traductions (traductions de tous les éléments d'interfaces définis dans la maquette : on les édite dans la l'onglet administration > administrer les traductions du site. On peut ajouter des traductions du site dans différentes langues + renseigner les traductions de toutes les variables dans ces langues.

3. La variable Lodelscript `[#SITELANG]` contient la langue de navigation du site (par défaut elle prend la valeur définie comme langue principale dans les métadonnées du site : onglet administration  > options du site). En fonction de la variable `[#SITELANG]` Lodel utilisera la valeur des variables de traductions dans la langue correspondante.

4. le paramètre "lang" à passer en GET dans l'url qui redéfinit la valeur de la variable Lodelscript `[#SITELANG]` . Ex. http://monsite_sous_lodel.com/?lang=de définira `[#SITELANG]` à "de" (les variables de traductions "de" seront utilisées)  et il est possible d'utiliser une syntaxe Lodelscript de ce type `[#RESUME:#SITELANG]` pour afficher le résumé dans la langue de navigation. Attention, `[#SITELANG]` ne prend la valeur du paramètre lang que lorsqu'on navigue dans le site  en étant non-logué. Dans le cas contraire, c'est la langue de l'interface définie pour l'utilisateur loguée  qui définie la variable `[#SITELANG]`. Pour faire des tests, une solution consiste à utiliser 2 navigateurs dont 1 non-logué dans Lodel.

# Liste des messages d'erreur
## Messages renvoyés par le parseur LodelScript

`Unable to read file $in` :

Lodelscript tente de lire un fichier sans y parvenir. Vérifiez qu'il existe et si il n'y a pas de problèmes de droits.

`Invalid refresh time "$refresh"`

Le temps de refesh n'est pas valide.

`the macro file fichier.html does exist`

Le fichier de macro n'existe pas. Vérifiez.

`this file contains more closing tags than opening tags`

Une erreur de codage, certaines <BALISES> sont fermées mais pas ouvertes. Vérifiez votre fichier.

`cannot write file $out`

Erreur d'écriture : vérifiez les droits sur le répertoire.

`internal error in parse_main. Report the bug`

Bogue important. Contactez l'équipe de Lodel : lodel@lodel.org

`The closing tag ".$this->arr[$this->ind]." is malformed`

Erreur dans l'écriture d'une balise.

`internal error in parse_main. Report the bug`

Bogue important. Contactez l'équipe de Lodel : lodel@lodel.org

`name already defined in loop $name`

Vous utilisez deux fois le même attribut NAME.

`Attribut LIMIT should occur only once in loop $name`

Vous ne pouvez utilisez LIMIT qu'une seule fois dans une boucle.

`Attribut GROUPY should occur only once in loop $name`

Vous ne pouvez utilisez GROUPBY qu'une seule fois dans une boucle.

`Attributs SELECT and DONTSELECT are exclusive in loop $name`

Vous ne pouvez pas utiliser à la fois SELECT et DONTSELECT dans la même boucle.

`unknown attribut "$result[1]" in the loop $name`

Attribut inconnu dans votre boucle.

`the name of the loop on table(s) nom is not defined`

L'attribut NAME de la LOOP n'est pas défini.

`loop $name cannot be defined more than once`

Deux boucles ne peuvent pas avoir le même nom.

`internal error in parse_loop. Report the bug`

Bogue important. Contactez l'équipe de Lodel : lodel@lodel.org

`In loop $name, the block $state is defined more than once`

Un bloc (DO, ALTERNATIVE, ou autre) est défini plus d'une fois dans une boucle.

`<TAG> not closed in the loop $name`

Une balise n'est pas fermée dans une boucle.

`unexpected <BALISE> in the loop $name`

Une balise inattendue dans une boucle.

`end of loop $name not found`

La boucle n'a pas de fin.

`In the loop $name, a part of the content is outside the tag DO MACRO tag malformed`

Erreur de syntaxe dans votre boucle.

`the macro $result[2] is not defined`

Vous appelez une macro non définie.

`IF have no COND attribut`

IF sans COND

`ELSE found twice in IF condition`

Vous utilisez deux fois ELSE.

`incorrect tags "".$this->arr[$this->ind]."" in IF condition`

Erreur de syntaxe dans un IF

`IF not closed`

Il manque un </IF>

`LET have no VAR attribut`

LET sans VAR.

`Variable "$result[1]"in LET is not a valide variable`

La variable que vous voulez assigner avec LET n'est pas valide. Probablement un problème de nom.

`</LET> expected, <BALISE> found`

Le LET est mal fermé.

`</ESCAPE> expected, <BALISE> found`

ESCAPE est mal fermé.

## Messages renvoyés par le parseur PHP ou SQL

`Fatal error: Call to undefined function: boucle_ma_boucle()`

Vous essayer d’appeler une boucle prédéfinie qui n’existe pas, vérifiez le nom de la boucle.

`You have an error in your SQL syntax near …`

Une boucle base de données contient des informations qui ne correspondent pas à la base de données, vérifiez que les attributs TABLE et WHERE contiennent bien des tables et des champs existants dans la base de données.

# Les tags wiki par défauts

La syntaxe wiki pouvant être utilisée par lodel est la suivante :
## de types bloc

* Paragraphe : 2 sauts de lignes
* Trait HR : ==== (4 signes "égale" ou plus) + saut de ligne
* Liste : une ou plusieurs * ou - (liste simple) ou #(liste numérotée) par item + saut de ligne
* Tableaux : | texte | texte. | encadré par des espaces (sauf pour le premier) = caractere séparateur de colonne, chaque ligne écrite = une ligne de tableau
* sous titre niveau 1 : !!!titre + saut de ligne
* sous titre niveau 2 : !!titre + saut de ligne
* sous titre niveau 3 : !titre + saut de ligne
* texte préformaté : un espace + texte + saut de ligne
* citation (blockquote) : un ou plusieurs > + texte + saut de ligne
* Définitions : ;terme : définition + saut de ligne (le : doit être encadré par des espaces)

## de type inline

* emphase forte (gras) : __texte__ (2 underscores)
* emphase simple (italique) : ''texte'' (deux apostrophes)
* Retour à la ligne forcée : %%%
* Lien : [ nomdulien | lien | langue | déscription (title)]
* Image : (( lien vers l'image | textalternatif | position | longue déscription )) . valeurs de position : l/L/g/G => gauche, r/R/d/D =>droite, rien : en ligne. Dans le code généré, c'est une balise style qui est crée, et non un attribut align (obsolète).
* code : @@code@@
* citation : ^^phrase|langue|lien source^^
* reférence (cite) : {{reference}}
* acronym : ??acronyme|signification??
* ancre : ~~monancre~~
