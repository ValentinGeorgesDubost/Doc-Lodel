Introduction
------------

Lodel a été historiquement conçu pour mettre en ligne des revues scientifiques existant déjà en version papier. Cependant, le logiciel a désormais évolué vers une plus grande généricité. Son fonctionnement n’est plus seulement tourné vers les revues et il permet la mise en ligne d’autres publications scientifiques, comme les colloques, mais également d’autres types de sites web, comme des blogs (sites personnels), des expositions virtuelles ou des photoblogs. L’équipe de Lodel.org a défini un vocabulaire général afin de décrire chaque objet manipulé par le logiciel de façon assez abstraite pour être utilisable dans différents contextes. Prenons un exemple pour illustrer les notions décrites dans ce chapitre : la revue fictive Sociométrie contemporaine.

La revue Sociométrie contemporaine publie quatre numéros par an. Chaque numéro comprend une quinzaine d’articles. Il y a parmi eux des articles de fond ainsi que des comptes rendus de lecture. Chaque numéro est divisé en trois parties : Recherche, Chroniques, et Comptes Rendus. Les responsables de la revue aimeraient apporter une plus-value à leur publication en publiant des dossiers annuels qui seront alimentés tout au long de l’année par des retranscriptions de communications lors de séminaires de recherche. Deux ensembles de publications sont donc à envisager : le premier pour les numéros trimestriels, le second pour les dossiers annuels.

Le modèle éditorial
-------------------

Lors de l’installation de Lodel, l’utilisateur doit choisir un modèle éditorial (ME). Cette action, d’apparence anodine, est décisive pour la suite des opérations. Le modèle éditorial définit en effet le type de site que vous allez utiliser. A l’installation, il vous propose un certain nombre de types de sites prédéfinis. En juillet 2004, Lodel vous proposait de créer un site sur le modèle d’une revue de Revues.org ou un site sur le modèle d’un blog (site personnel). En choisissant un modèle éditorial ou en en important un autre, l’ensemble des champs et des options de votre site seront définis. Qu’est-ce qui différencie les modèles éditoriaux entre eux ? Les champs ne sont pas les mêmes : en effet, si une revue scientifique a besoin de résumés dans diverses langues, un blog n’en a pas besoin. Le champ « résumé », de type « texte multilingue » n’est donc pas disponible dans un ME dédié aux blogs. De même, dans le modèle éditorial scientifique, vous pouvez créer des collections, des volumes et des numéros, tandis que dans un modèle éditorial de type « blog », vous ne pouvez créer que des rubriques et des annuaires de liens. Il en est de même pour les index : quatre types d’index sont prévus dans le modèle scientifique, contre seulement deux dans le modèle de blog. Par ailleurs, le texte d’un blog est en général relativement simple et l’importation de fichiers issus d’un traitement de texte est exagérément complexe pour ce type d’usage, alors que, dans le cadre des documents scientifiques, plus complexes, cette possibilité est fondamentale. Le modèle « blog » désactivera donc l’importation des documents issus d’un traitement de texte pour permettre une saisie dans un formulaire en ligne, tandis que le modèle « revue scientifique » prévoira systématiquement une importation de documents issus de Word ou d’OpenOffice.org. Ainsi, le modèle éditorial définit à la fois le contenu des documents et des publications (on parle de champs), le type de documents et de publications, mais également l’ensemble des options et préférences du site. Dans le cas d’un usage où la rapidité et la simplicité l’emportent, il est opportun de choisir le modèle « blog ». Dans le cas de besoins complexes le modèle « revue scientifique » est plus adapté, mais il nécessite un apprentissage un peu plus élaboré et le traitement de chaque document est plus long.

Le modèle éditorial est une fonctionnalité très puissante, modifiable à volonté par toute personne disposant du niveau d’autorisation des administrateurs Lodel (la personne qui a installé le logiciel). Proportionnellement à sa puissance, les conséquences de sa modification peuvent être considérables, parfois très graves. Par exemple, si vous décidez de modifier le type du texte d’un document en le passant de « texte long » à « texte court », vous allez raboter l’ensemble de vos documents pour qu’ils puissent entrer dans le nouveau format. Le retour à un « texte long » ne rétablira jamais le contenu initial des documents. De même, le modèle éditorial ayant une influence sur la définition du schéma XML, superstructure du document, la modification du modèle éditorial modifiera l’ensemble des fichiers XML décrivant le site et le schéma XML du site. Vous prenez donc le risque d’introduire des incompatibilités entre sites. Cela n’est pas important dans certains contextes, mais se révèle essentiel dans d’autres. D’une façon générale, utiliser la puissance de la configuration du modèle éditorial est fortement recommandé. Il est également recommandé de diffuser vos modèles éditoriaux sous licence libre sur Internet et de les soumettre à l’équipe de développement de Lodel.org, qui pourra éventuellement les diffuser à l’intérieur de la prochaine version de Lodel. Cependant, la plupart du temps, il vous suffira d’utiliser un modèle éditorial déjà conçu par quelqu’un d’autre, car la définition d’un ME est relativement complexe et impose une réflexion ainsi qu’une connaissance de certaines contraintes liées au XML.

Les publications
----------------

Les deux entités essentielles du site sont le document et la publication. Les documents constituent le contenu principal du site : les articles d’une revue, les communications d’un colloque, les billets d’un blog. Les publications contiennent les documents : les numéros d’une revue, les journées d’un colloque, les rubriques d’un blog.

La revue Sociométrie contemporaine comporte deux publications appelées collections. La première contient l’ensemble des numéros et la seconde contient les comptes rendus des séminaires mensuels. La collection « Revue » contient des numéros qui ont pour type « numéro » et la collection « Séminaires » contient une rubrique par année.

Le schéma ci-dessous montre les publications (cellules grisées) qui contiennent les documents que sont les articles de la revue et les comptes rendus des séminaires.

La structuration de la revue Sociométrie contemporaine

Les documents
-------------

Dans Lodel, ce sont les documents qui contiennent les textes publiés. Dans une revue on peut trouver différentes sortes de documents : des comptes rendus, des articles, des notes de lecture… Les types de documents permettent de distinguer ces documents entre eux, de leur faire subir des traitements différents et de leur affecter une mise en forme (template) adaptée.

Les types de documents
----------------------

A chaque type de document est associé un template (ou « maquette »), c’est-à-dire un modèle graphique de document. Ainsi, les articles peuvent avoir une mise en forme différente des comptes rendus. Les types de documents sont également utilisés dans les sommaires ou dans les index, pour classer les documents. Les types de documents font partie du modèle éditorial. Si vous souhaitez les modifier, il faut disposer des droits d’administrateur Lodel.

Les documents annexes
---------------------

Les documents annexes peuvent être attachés à des documents ou des publications. On les utilise pour annexer un document particulier à une entité. Ainsi, on peut associer à un document un lien vers un site web ou vers un fichier au format PDF, vidéo ou image. Voici les types de documents annexes possibles :

lien vers un site externe
lien vers un document interne au site
lien vers une publication interne au site
lien vers un fichier : ce fichier peut être de format très divers (vidéo, son, image, pdf…)

Les index
---------

Les index permettent de classer les documents en fonction des métadonnées qui sont associées aux documents. Par exemple, dans le modèle éditorial de Revues.org, il est possible d’associer des thèmes à chaque document pour obtenir un classement par thème.

La revue Sociométrie contemporaine souhaite classer par discipline, sous-discipline et thématique l’ensemble de ses documents. Elle utilise l’index par thèmes du ME de Revues.org dans lequel elle saisit l’ensemble des disciplines. Elle associe ensuite à chaque discipline plusieurs sous-disciplines auxquelles elle attribue, enfin, des thématiques. Chaque document est associé à plusieurs thématiques.

Il est possible de saisir les entrées d’index dans chaque document DOC ou SXW. Il est également possible d’utiliser l’interface en ligne pour sélectionner les entrées d’index qui sont associées à chaque document.

Attention. Lors du rechargement d’un fichier, l’ensemble des informations saisies en ligne est effacé. Il est donc recommandé de saisir les entrées qui doivent être associées au document directement dans le traitement de texte.

Une fois les informations correctement saisies, Lodel génère des index. Par exemple, l’index par auteur est accessible à l’adresse personnes.html?type=auteur. Chaque index est mis à jour à chaque ajout ou suppression de document.

La définition du nombre et des types d’index fait partie du modèle éditorial.

Les statuts de publication
--------------------------

Dans l’édition traditionnelle, un article peut avoir deux états : publié ou non publié. Il est naturel que l’on retrouve ces statuts sous Lodel. Les documents non publiés ne sont accessibles qu’aux personnes identifiées dans Lodel. Les internautes n’y ont jamais accès. Seuls les documents publiés sont accessibles aux internautes. Lodel propose deux statuts supplémentaires, permettant une gestion plus fine des documents. Pour chaque publication et chaque document, quatre statuts sont disponibles : Brouillon, Prêt à publier, Publié, Publié protégé. Seul l’éditeur ou l’administrateur peuvent changer le statut d’une entité.

- Prêt à publier
Le statut « Prêt à publier » indique que le document ou la publication n’est pas visible par l’internaute lorsqu’il navigue sur le site. En revanche, l’utilisateur de Lodel qui est connecté peut voir le document, le travailler, le modifier. Par défaut, les publications que l’on crée ou les documents que l’on charge sont non publiés. Cela permet de procéder à une relecture avant la publication.

- Publié
Quand un document a pour statut « Publié », il est visible par l’internaute sur le site.

- Publié protégé
Le statut « Publié protégé » est un niveau supplémentaire qui permet de sécuriser le processus de publication en rendant sa dépublication difficile. Ceci permet d’éviter toute publication involontaire ou irréfléchie. La dépublication est une action importante qu’il ne faut pas effectuer avec légèreté. Lorsqu’un document a été publié, il est visible sur le site, un visiteur peut donc le voir et le citer ou en conserver l’adresse pour son usage personnel. La dépublication de cette page la rendra inaccessible pour l’internaute. Cela rompra la chaîne hypertextuelle et contredira le principe de citabilité. La dépublication est donc possible techniquement mais déconseillée d’un point de vue éditorial.

- Brouillon
Le statut « Brouillon » est le pendant exact du statut « Publié protégé ». En effet, il s’agit aussi d’une protection, mais cette fois, lorsque le document n’est pas encore publié. Si on lui donne le statut « Brouillon », il ne pourra pas être publié directement : il faudra d’abord retirer son statut de brouillon. Cela permet d’éviter toute publication intempestive d’un document sur lequel il reste encore du travail à faire. Ce procédé est particulièrement déterminant dans le cas de la publication d’une publication (un numéro par exemple). En effet, le processus de publication est récursif : en publiant une publication, on publie par la même occasion l’ensemble des publications subordonnées qu’elle contient : les publications « enfants », que ce soit des rubriques, des regroupements ou des documents. Seuls les documents et les publications ayant le statut « Brouillon » échappent à la publication dans ce cas.

- La publication différée du texte intégral
Il est possible, lorsqu’on charge un document dans Lodel, de décider de ne pas le publier en texte intégral avant plusieurs mois. On peut alors programmer sa publication en inscrivant dans Lodel la date officielle de publication du document. Jusqu’à cette date, le document sera disponible sur le site, mais ne seront visibles que ses métadonnées et son résumé.

Les niveaux d’utilisateurs et le processus de validation
--------------------------------------------------------

Dans le travail de création, de maintenance et de mise à jour d’un site, les manipulations à effectuer sont multiples : l’importation des documents, la publication de ces documents, la structuration du site, la maintenance des templates…

Il est rare que ces rôles soient tenus par une seule et même personne. Ainsi le secrétaire de rédaction sera chargé de l’importation des documents, le rédacteur en chef aura la responsabilité de la publication et le webmaster devra s’occuper du travail sur les templates. On peut encore imaginer que des membres d’un comité de rédaction souhaitent bénéficier d’un accès au site en développement afin de visualiser les documents non encore publiés.

Ces différents rôles à jouer sur le site impliquent des différences de droits d’accès. Par exemple, la personne qui importe les documents n’a pas nécessairement l’autorité nécessaire pour publier ou dépublier les documents du site. Par conséquent, il ne faut pas que cette possibilité lui soit accordée. Lodel propose donc cinq statuts d’utilisateurs qui correspondent à cinq niveaux d’usage de Lodel : il permet ainsi de limiter le champ d’intervention aux domaines de stricte compétence, de ne pas offrir à un utilisateur de valider des actions qui sont hors de sa compétence technique ou éditoriale.

Pour chaque niveau d’utilisateur, les boutons correspondant aux actions non autorisées sont inactifs mais restent visibles. Ainsi, quel que soit le niveau d’accès de l’utilisateur, il peut avoir un aperçu complet des fonctionnalités de Lodel même s’il ne peut les utiliser directement.

Exemple : les boutons dont l’accès n’est pas autorisé.

Le type d’accès de l’utilisateur apparaît sous la forme d’une icône de couleur dans l’interface en haut à droite de l’écran.

- Visiteur
C’est le niveau d’accès le plus restrictif. Il permet à la personne connectée à Lodel de naviguer au sein du site et de l’interface d’édition mais aucune action ne lui est permise. Il ne peut avoir qu’un statut de spectateur. Par exemple, ce niveau d’accès peut être attribué à un membre du comité de rédaction d’une revue.

- Rédacteur
Le « rédacteur » peut ajouter des documents au site en les important via l’interface de chargement. Aucune autre action ne lui est permise, il ne peut ni publier les documents, ni les détruire. Ce niveau d’accès correspond par exemple au secrétaire de rédaction qui n’a en charge que le stylage et l’importation des documents.

- Editeur
Le niveau « éditeur » convient par exemple au rédacteur en chef de la publication. C’est lui qui décide quel document doit être publié, dépublié, détruit.
L’éditeur peut aussi créer les publications, dans le modèle éditorial de Revues.org il s’agit de collections, de rubriques ou de regroupements ; déplacer les documents d’une publication à une autre. Il gère la structuration éditoriale du site.

- Administrateur
L’administrateur, à l’inverse du visiteur, possède tous les droits. Il peut accéder à toutes les fonctionnalités disponibles dans l’interface d’édition du site. Il gère l’ensemble du site, les différents utilisateurs, les options définies dans l’interface d’administration. Ce niveau correspond à celui du webmaster.

- Administrateur Lodel
L’administrateur Lodel possède deux droits supplémentaires par rapport à l’administrateur simple. Il peut modifier le modèle éditorial du site, et dans le cas des multisites, l’administrateur lodel peut circuler d’un site à un autre. Il a automatiquement accès à tous les sites.

Notions de stylage pour Lodel avec un traitement de texte
---------------------------------------------------------

- Les styles d’un traitement de texte
Les styles définissent les paramètres de composition d’un paragraphe ou d’un ensemble de mots. Ils sont utilisés depuis les origines par les logiciels de traitement de texte et par les logiciels de PAO (publication assistée par ordinateur). Ils permettent de caractériser de façon harmonieuse l’apparence des titres, des légendes, des notes de bas de page, etc. Correctement utilisés, ils simplifient et accélèrent la mise en forme de documents longs. Ils permettent également au logiciel de traitement de texte de construire une table des matières ou un sommaire.
Lodel s’appuie sur les styles définis dans votre traitement de texte pour identifier la fonction de chaque bloc de texte. Il s’en sert comme information sémantique, afin de détecter le titre, l’auteur, les mots clés, le résumé, etc. Lodel ne récupère pas la mise en forme de chaque style, mais seulement le nom du style, dont la mise en forme sera commandée par la feuille de style CSS (voir ci-dessous). Il récupère en revanche les mises en forme locales (voir ci-dessous).

- Style de caractère, style de paragraphe

On différencie deux types de styles : les styles de caractère qui ne portent que sur un ou plusieurs mots, et les styles de paragraphe qui portent sur tout un paragraphe. Par exemple, l’italique, le gras ou l’exposant sont des styles de caractère : ils ne portent que sur un mot, un groupe de mots ou une lettre en leur ajoutant une information supplémentaire. C’est le cas pour le « e » placé en exposant dans « XIXe siècle ». Le style de caractère affecte donc le texte que l’on a sélectionné, situé à l’intérieur d’un paragraphe.

Les styles « Titre », « Résumé », « Normal » sont des styles de paragraphe. Ils ne peuvent porter que sur l’ensemble du paragraphe. Ainsi, il est impossible de faire cohabiter le style « Titre 1 » et « Titre 2 » dans le même paragraphe.

La mise en forme locale
-----------------------

Les traitements de texte permettent l’ajout de mises en forme locales sur un style défini. Par exemple, Word permet de modifier un paragraphe ayant le style « Normal » en lui ajoutant localement la couleur rouge. Word crée alors un style s’appelant « Normal + Rouge ». Il a créé une mise en forme locale appliquée au style « Normal ». Par principe, Lodel considère que la mise en forme locale que vous avez ainsi ajoutée est intentionnelle. Il ajoutera donc la couleur rouge au paragraphe concerné. Il peut cependant arriver qu’une mise en forme locale soit le résultat de l’histoire complexe d’un fichier. De nombreux changements d’ordinateur, d’utilisateur, de logiciel de traitement de texte, de copier-coller de textes issus du web ou de logiciels de courrier électronique et bien d’autres vicissitudes produisent la multiplication des mises en forme locale involontaires qu’il faut éliminer. Le chapitre 5 explique comment éliminer ces informations non désirées.

Les styles sur Internet : les CSS
---------------------------------

Pour afficher les documents importés depuis un traitement de texte, Lodel utilise les feuilles de styles dites CSS (« Cascading style sheets »). C’est la modification de chaque style CSS qui modifie l’apparence des documents.

Exemple : Dans un traitement de texte, vous pouvez avoir défini le style « Titre » en « Police Times New Roman, 16 pt, couleur noire ». Lodel ne récupère que le nom de style (« Titre ») et lui applique l’apparence du style CSS défini par le webmaster : « Arial, 12 px, couleur noire ».

Notions complémentaires
-----------------------

- Les mini textes
Les mini textes sont des « petits textes d’actualité » associés à une page particulière, en général la page d’accueil du site. Ces éléments ne sont pas sauvegardés au format XML, ni dans la base de données. Ils ne sont pas considérés comme des publications à part entière, ne disposent pas d’une URL spécifique et ne sont donc pas citables. Les mini textes ne sont attachés à aucune publication particulière ni à aucun document particulier, mais à un ou plusieurs templates. Ces petites notes permettent au webmaster d’afficher de façon très rapide des informations évolutives de petite taille sur le site.
