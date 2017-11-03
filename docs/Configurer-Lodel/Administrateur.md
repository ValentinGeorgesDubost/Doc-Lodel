Configuration
=============

Gérer les utilisateurs
----------------------

La page « Utilisateurs et droits »
----------------------------------

Les informations sur les utilisateurs du site sont affichées sur la page « Gestion des utilisateurs ». Il est possible de gérer les sessions, de modifier les comptes ou de les supprimer.

cliquer sur « Effacer le log des sessions » pour effacer l’historique des connexions à Lodel de cet utilisateur.
cliquer sur « Modifier » pour modifier le compte de l’utilisateur, il dirige vers la page « Edition d’un utilisateur »(voir ci-dessous).
cliquer sur « Supprimer » pour supprimer le compte. Le compte de l’utilisateur devenu inactif est déplacé dans une corbeille. Il est possible de le récupérer en cliquant sur « Récupérer » ou de le détruire définitivement en cliquant sur « Détruire ».

Ajouter un utilisateur
----------------------

Cette fonction dirige vers la page « Edition des utilisateurs », il faut renseigner les champs demandés puis définir le droit d’accès de ce nouvel utilisateur sur Lodel : Visiteur, Rédacteur, Editeur ou Administrateur.

Cette page permet d’ajouter, de modifier, ou de supprimer un utilisateur.

Informations générales sur l’utilisateur
----------------------------------------

Vous devez tout d’abord fournir certaines informations pour identifier l’utilisateur :

Login : indiquez un identifiant qui devra être transmis à l’utilisateur

Il est préférable que les logins soient composés au maximum des 8 premiers caractères du nom de la personne, et ne contiennent pas d’accent, de trait d’union ou d’espace.

Exemple : Alain Dépondupon login: depondup

Mot de passe : indiquer un mot de passe différent de l’identifiant; il devra être transmis à l’utilisateur

Conseil : choisissez une suite de 7 à 8 caractères, mêlant majuscules et minuscules, chiffres et/ou caractères de ponctuation

Informations spécifiques à Lodel
--------------------------------

Ce bloc est tout aussi indispensable que le premier. Il vous permet en effet de définir :

la langue de l’utilisateur
son privilège : ce sont les droits d’accès dont il dispose (visiteur, rédacteur, éditeur, administrateur)
la complexité de l’interface associée à chaque utilisateur
Par défaut, le privilège de tout nouvel utilisateur est Visiteur.

La complexité de l’interface par défaut est avancée. Les différents niveaux de complexité de l’interface permettent de paramétrer l’affichage de certains formulaires, qui comprendront un niveau plus ou moins élevé de champs selon la complexité choisie.

Les informations optionnelles
-----------------------------

Ce bloc permet d’entrer un certain nombre d’informations optionnelles, utiles par exemple dans le cas d’équipes travaillant à distance : contacts complets (téléphone, adresse de messagerie instantanée…)

Une fois toutes les informations entrées dans le formulaire, cliquez sur « ajouter ». VOus pouvez bien sûr modifier par la suite ces informations, à partir de la page d’édition des utilisateurs.

Modifier les informations sur un utilisateur
--------------------------------------------

Il est possible à tout moment de modifier les informations sur les utilisateurs, à partir de la page d’édition des utilisateurs. Cliquez sur « modifier », faites les modifications nécessaires, puis validez.

Editer les options du site
--------------------------

Cette fonction permet de déterminer les options générales du site. Elle permet, par exemple, de définir des variables de Lodelscript qui pourront servir dans les templates (Cf Chapitre 7).

La page « Options »
-------------------

Trois options sont disponibles par défaut. Il s’agit d’un groupe d’options configurant le serveur dédié à la conversion de documents issus du traitement de texte vers XML utilisé par Lodel. Ces options définissent l’adresse d’accès au serveur, son nom, et, optionnellement, le mot de passe permettant d’y accéder.

Le lien « ajouter une option » dirige vers la page « Edition des options » (voir, ci-dessous, le paragraphe « ajouter une option ») Pour chaque option trois éléments doivent être définis dans les champs destinés à cet effet :

le Nom : le nom de l’option doit uniquement contenir des lettres non accentuées, des chiffres et des espaces soulignés ou undescores (_). Cet élément permet d’identifier l’option dans les templates.
la Valeur : la valeur de l’option est l’élément qui la caractérise à l’affichage par les templates.
le Type : le type de l’option définit la nature de l’option. Il est possible de choisir parmi 6 types déterminés dans la liste déroulante : texte, mot de passe, URL, mail, couleur ou nombre entier. En fonction du type indiqué une vérification de la valeur est effectuée. Par exemple, si vous indiquez le type URL en omettant de saisir « http:// », un message d’erreur apparaîtra lorsque vous validerez l’ajout de l’option.
Pour modifier l’option :

cliquer sur « Editer » pour obtenir la page « Edition des options » (voir le paragraphe suivant).Pour supprimer l’option :
cliquer sur « Supprimer »
La page « Edition des options »:

Pour modifier une option, il est possible de l’éditer depuis la page « Options » (voir le paragraphe ci-dessus). Une fois parvenu sur la page « Edition des options » :

cliquer sur « Modifier » pour modifier le Nom, la Valeur, le Type ou le statut (« normal » ou « protégée ») de l’option.
cliquer sur « Annuler » pour annuler l’opération et retourner sur la page « Options ».
cliquer sur « Supprimer » pour supprimer l’option ajoutée
Ajouter une option

Il est possible d’ajouter une option depuis la page « Options »(voir ci-dessus). Une fois parvenu sur la page « Edition des options ». Renseigner les champs suivants :

Nom : inscrire le nom de l’option.
Type : choisir le type de l’option dans la liste déroulante.
Protège : il est possible de choisir le statut protégé en cochant la case indiquée.
Puis,

cliquer sur « Ajouter » pour créer l’option sur la page« Options ».
cliquer sur « Annuler » pour annuler l’opération et retourner sur la page « Options »
cliquer sur « Supprimer » pour effacer les opérations.
Lorsque l’option est créée, inscrire sa valeur dans le champ destiné à cet effet sur la page « Options », puis :

cliquer sur « Modifier » pour enregistrer.
cliquer sur « Modifier et terminer » pour enregistrer et retourner sur l’espace « Administrer »
cliquer sur « Annule » : annuler l’opération et retournersur l’espace « Administrer »

Le Modèle éditorial (à compléter)
---------------------------------

Présentation
------------

Les contenus d’un site propulsé par Lodel sont stockés dans une base de données. Le modèle éditorial (ME) est une modélisation des entités contenues dans la base de données.

Le modèle éditorial définit à la fois le contenu des documents et des publications (on parle de champs), le type de documents et de publications, mais également l’ensemble des options et préférences du site.

Le modèle éditorial est une fonctionnalité très puissante, modifialbe à volonté par tout administrateur du site. Proportionnellement à sa puissance, les conséquences de sa modification peuvent être considérables, parfois très graves.

Par exemple, si vous décidez de modifier le type du texte d’un document en le passant de « texte long » à « texte court », vous allez raboter l’ensemble de vos documents pour qu’ils puissent entrer dans le nouveau format. Le retour à un « texte long » ne rétablira jamais le contenu initial des documents. De même, le modèle éditorial ayant une influence sur la définition du sch&ma XML, superstructure du document, la modification du modèle éditorial modifiera l’ensemble des fichiers XML décrivant le site et le schéma XML du site.

Lodel.org met à disposition un Modèle éditorial prédéfini, qui permet une utilisation poussée des potentialités de Lodel.

Les entités
-----------

Les modèles éditoriaux d’un site Lodel sont composés de différentes entités.

Les deux entités principales sont le document et la publication. Les documents constituent le contenu principal du site (par exemple : les articles d’une revue, les actualités). Les publications contiennent les documents, certaines peuvent également contenir d’autres publications.

Il existe différents types de publications et différents types de documents, ce qui permet d’organiser les contenus en fonction de leur teneur (article scientifique, actualité, texte de présentation…), et de leur appliquer des traitements et une mise en forme spécifiques.

On peut ajouter à la base du site cinq entités : un type de publication (collection) et quatre types de document (éditorial, article, annonce et actualité et présentation).

La collection est la première subdivision d’une revue en ligne élaborée avec le modèle éditorial de Revues.org. Elle se crée à la base du site et est destinée à recevoir volumes, numéros, rubriques, colloques ainsi qu’éditoriaux, articles, annonces et actualités, brèves et présentations.

Un volume, un numéro, une rubrique et un colloque peuvent contenir un volume, un numéro, une rubrique, un colloque, un regroupement, un article, une annonce et actualité, un éditorial, une brève, un compte rendu, une note de lecture, une présentation, une chronique et un article vide. Les publications de type rubrique, numéro, volume et colloque peuvent contenir un nombre illimité de publications. Un regroupement peut recevoir des documents tels qu’articles, annonces et actualités, éditoriaux, brèves, compte rendus, notes de lecture, présentations, chroniques et articles vides. Un regroupement ne peut par conséquent pas recevoir de publications.

Gestion des index
-----------------

Cet espace permet de gérer les index en y intégrant des entrées d’index, ou en modifiant et supprimant des entrées déjà enregistrées.

Index linéaires et index hiérarchiques
--------------------------------------

Lodel est capable de gérer deux types d’index : les index linéaires, plaçant toutes les entrées créées sur un même niveau, et les index hiérarchiques, permettant de créer des entrées de niveaux hiérarchisés.

Le modèle éditorial de Revues.org comprend deux types d’index linéaires, l’index par atueur et l’index par mots clés, et trois types d’index hiérarchiques, les index chronologique, géographique et thématique.

L’index par auteur est généré dynamiquement par Lodel.

En revanche, tous les autres types d’index doivent être constitués par l’utilisateur.

Il existe trois manières d’attribuer des mots-clés à un document (Cf chapitre 3). L’espace « Administrer » permet de créer des index sous forme de thesaurus, préalablement au traitement des documents.

Index linéaires
---------------

- AJOUTER UNE ENTRÉE

Cette fonction dirige vers la page « Edition d’une entrée », où vous devez saisir le nom ou l’expression de l’entrée choisie, sélectionner la langue du nom ou de l’expression saisis et cocher la case « entrée permanente » si vous souhaitez protéger l’entrée ajoutée.

- LA PAGE « INDEX »

La page « Index » présente la liste par ordre alphabétique des mots-clés que vous avez ajoutés. Chaque entrée présente la langue sélectionnée correspondante et le statut, Normal ou Protégée, que vous lui avez attribué. Il est possible de modifier l’ensemble des renseignements correspondant à l’entrée saisie en cliquant sur le bouton Modifier ou de supprimer l’entrée en cliquant sur le bouton Supprimer

Index hiérarchiques
-------------------

- AJOUTER UNE ENTRÉE

Cette fonction dirige vers la page « Edition d’une entrée », où vous devez saisir le nom ou l’expression de l’entrée choisie.

Vous pouvez éventuellement faire correspondre une abréviation à cette entrée.

Dans un index chronologique, par exemple :

Entrée : Dix-neuvième siècle

Abréviation : IXème

Pour obtenir des niveaux d’entrée hiérarchisés, vous devez sélectionner l’entrée parente de l’entrée saisie plus haut.

Dans un index géographique, par exemple :

Pour les entrées « France », « Vaucluse », « Avignon », à l’entrée « Avignon » correspondra l’entrée parente « France/Vaucluse ».

Le nombre de barres verticales placé en début de ligne sous l’entrée précedente indique le niveau hiérarchique d’une entrée.

Vous pouvez également sélectionner la langue de l’entrée saisie et cocher la case « entrée permanente » si vous souhaitez protéger l’entrée ajoutée.

Gestion d’un index linéaire : l’index par mots clés
---------------------------------------------------

Le lien « Ajouter une entrée » pointe vers la page « Edition d’une entrée : Index par Mots clés » qui permet de définir l’entrée à ajouter.

Il est possible de modifier une entrée : le lien Modifier pointe vers la page d’Edition d’une entrée expliquée ci-dessus ; ou de supprimer une entrée.

La suppression d’une entrée est définitive. Il est possible de supprimer une entrée lorsqu’elle ne contient pas d’autres entrées, et lorsque son statut est « Normal ». Lorsqu’une entrée a le statut « Protégée » il faut modifier son statut pour pouvoir la supprimer, en cliquant sur le lien Modifier, puis en décochant le champ Entrée permanente.

Gestion d’un index hiérarchique : l’index chronologique
-------------------------------------------------------

Le lien « Ajouter une entrée » pointe vers la page « Edition d’une entrée : « Index chronologique » qui permet de définir l’entrée à ajouter.

Il est possible de modifier ou de supprimer une entrée (voir le paragraphie ci-dessus). Lorsqu’une entrée parente contient des sous-entrées (ex : XXeme siècle>Années 30), elle est protégée. Pour pouvoir supprimer l’entrée parente, il faut donc supprimer les entrées enfants

NB : les entrées enfants sont repérables visuellement par une barre verticale placée devant le nom de l’entrée.
