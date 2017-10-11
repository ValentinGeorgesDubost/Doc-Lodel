F.A.Q
=====

Qu’est-ce que Lodel ?
---------------------

Lodel est un logiciel d’édition électronique. Il est simple d’utilisation, et facile à adapter à des usages particuliers. 
C’est un logiciel libre, sous licence GPL développé par l’équipe de Revues.org. Il est librement téléchargeable sur <http://sourceforge.net/projects/lodel/>. C’est un CMS (logiciel de gestion de contenu).

Qu’est-ce qu’un CMS ?
---------------------

Les systèmes de gestion de contenu ou CMS (de l’anglais Content Management System) sont une famille de logiciels de conception et de mise à jour dynamique de site Web partageant les fonctionnalités suivantes :
- Ils permettent à plusieurs individus de travailler sur un même document
- Ils fournissent une chaîne de publication offrant par exemple la possibilité de mettre en ligne des documents
- Ils permettent de séparer les opérations de gestion de la forme et du contenu pour en savoir plus, voir la partie « survol du fonctionnement de Lodel »)
- Ils permettent de structurer le contenu

A quoi sert Lodel ?
-------------------
Lodel est un logiciel d’édition électronique : il prend en charge le processus de publication des textes, depuis le traitement de texte de l’utilisateur jusqu’à la mise en ligne.
Lodel a une double utilité :
- Il convertit des textes d’un format traitement de texte à un format web (XHTML)
- il génère automatiquement l’ensemble des métadonnées dont les publications ont besoin pour être correctement identifiées, indexées et référencées, notamment par les moteurs de recherche.

En quoi Lodel est-il différent d’autres logiciels de CMS ?
----------------------------------------------------------

Pour la plupart, les CMS sont fortement contraints au niveau du système de gestion : chacun d’eux détermine a priori ce qu’on peut faire et ce qu’on ne peut pas faire, et accepte rarement qu’on redéfinisse ses types d’objets.
Au contraire, Lodel intègre dans son principe de fonctionnement la possibilité, pour l’administrateur d’un site, de définir ses propres besoins :
- quels types de documents et de publications ?
- comment est organisée l’arborescence ? combien de rubriques, quels types d’index ?
L’ensemble de ces données de configuration constitue un modèle éditorial ; il peut être sauvegardé, échangé, modifié, restauré, échangé.
Pour les revues utilisant Lodel, la personnalisation de l’édition permise par l’utilisation de Lodel est donc très grande, ce qui leur permet d’affirmer leur identité à travers une maquette entièrement personnalisée.

A qui s’adresse Lodel ?
-----------------------

Lodel a d’abord été créé pour répondre à des besoins d’édition électronique en sciences humaines et sociales pour la fédération de revues scientifiques Revues.org.
Ce logiciel est donc particulièrement adapté à la publication de documents longs, complexes, fortement structurés (plusieurs niveaux de titres, blocs de citations), et permet de gérer efficacement notes de bas de page, tableaux, illustrations, des mises en forme locales (petites capitales, lettrines)…
Mais la grande souplesse de Lodel, et ses très nombreuses possibilités de personnalisation, permettent au logiciel d’être utilisé dans des situations très diverses : revues, bases de documents, sites événementiels et même…blogs !
Par ailleurs, son installation est très simple, et l’utilisation de configurations livrées avec le logiciel (modèle éditorial, maquette) permettent d’utiliser le logiciel sans connaissance informatique poussée.

A qui ne s’adresse pas Lodel ?
------------------------------

S’il propose des fonctionnalités plus avancées que la plupart des CMS, Lodel est moins adapté à certains usages précis, comme les débats autour d’un article, l’écriture coopérative… D’autres CMS comme DotClear, SPIP, WordPress ou PhpWiki conviennent à de nombreux usages simples et spécialisés pour lesquels Lodel n’est pas le logiciel le plus approprié.

Comment ça marche ?
-------------------

Lodel s’installe en quelques minutes chez un hébergeur web. Il est contrôlé à distance grâce à un navigateur web (Firefox, Internet Explorer)
Pour publier un document, deux solutions :
- soit les éditer directement en ligne (surtout pour les documents peu complexes)
- soit, le plus souvent, les préparer dans un traitement de texte (Word, OpenOffice.org, etc.)
Dans ce cas, les documents préparés dans un traitement de texte doivent être importés dans Lodel, qui les convertit en documents web. Lodel utilise pour cela un serveur basé sur les technologies d’OpenOffice.org, appelé servOO. Ce serveur permet de convertir des documents .doc, .rtf et .sxw en documents web (XML).

Dois-je avoir OpenOffice.org sur mon ordinateur ?
-------------------------------------------------

Non. Il suffit d’utiliser un logiciel de traitement de texte produisant des fichiers au format RTF, DOC ou SXW : Word, OpenOffice.

Est-ce que Lodel s’installe partout ?
-------------------------------------

Les hébergeurs gratuits (comme Free) imposent des restrictions d’hébergement qui empêchent l’installation de logiciels aussi puissants que Lodel. En revanche, Lodel peut être facilement installé chez de nombreux installeurs professionnels.
Pour en savoir plus sur l’installation de Lodel, nous vous renvoyons au [Manuel d’installation de Lodel]


Le modèle éditorial (ME) : Qu'est-ce que c'est ?
------------------------------------------------

Dans la plupart des CMS, on peut utiliser un nombre fini et défini de champs, comme le titre, le sous-titre, le texte et l’auteur du document.

Lodel est un CMS plus générique et conçu pour être évolutif : il vous permet de définir l’ensemble des champs dont vous avez besoin pour s'adapter parfaitement à vos besoins.

Par exemple, vous pouvez ajouter des résumés (dans diverses langues), des annexes, des images associées à un document, etc. Vous pouvez définir le style que vous utiliserez dans votre traitement de texte pour définir chaque champ, le nom du champ, la nature du champ et sa place dans le XML qui sera généré dynamiquement (schéma XML dynamique).

Vous pouvez ainsi mettre en ligne avec Lodel des textes, mais aussi des galeries photo, des nouvelles, des billets de blog, etc. Il vous suffit de définir votre propre modèle éditorial.

Est-on obligé de créer son propre modèle éditorial (ME) ?
---------------------------------------------------------

Il n’est pas recommandé de commencer à utiliser Lodel sans aucun Modèle éditorial prédéfini. L’équipe de Lodel.org met à votre disposition un ME Revues.org dédié à la publication structurée de textes longs. Si vous créez un ME dédié à un usage particulier, merci de le mettre à disposition du reste de la communauté pour permettre à d’autres utilisateurs de l’utiliser.

Est-ce que Lodel est gourmand en ressources ?
---------------------------------------------

La ressource la plus gourmande utilisée par Lodel est OpenOffice.org. Pour le reste, il est très économe en ressources systèmes car il utilise un système de cache.

Pourquoi et comment utiliser Lodelscript ?
------------------------------------------

LodelScript est un langage de template qui est inséré au milieu des balises HTML classiques. Il s’agit d’un langage de haut niveau qui permet d’afficher des variables ou des boucles. Ce langage permet de définir l’aspect graphique d’un site dynamique sans pour autant connaître de langage de programmation et de langage d’interrogation de bases de données comme SQL.

Lodelscript a été développé parallèlement au logiciel Lodel, mais peut très bien être adapté à d'autres systèmes de gestion des données.

Suis-je obligé de me servir de Lodelscript ?
--------------------------------------------

Non, il est possible d’utiliser directement PHP, mais Lodelscript est plus sûr et facilite la tâche du maquettiste.

Dispose t'on de maquettes prédéfinies ?
--------------------------------------------------------------------------------------------------

Oui. Vous pouvez démarrer en utilisant une maquette prédéfinie qui est livrée avec Lodel.

Est-ce qu'Openedition propose des formations utilisateurs pour Lodel ? Où postuler pour publier ma revue / collection Lodel sur Openedition ?
----------------------------------------------------------------------

<https://www.openedition.org/10837>
