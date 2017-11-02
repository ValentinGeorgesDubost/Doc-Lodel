ÉDITEUR
=======

Le niveau visiteur nous a permis de découvrir l’interface de Lodel 0.8
Le niveau rédacteur, de découvrir l’importation de documents sous Lodel
Les responsabilités de l’éditeur sont plus élevées. Les droits dont cet utilisateur dispose dans Lodel lui permettent en effet de gérer la publication dont il a la charge. Son travail correspond au travail traditionnel du rédacteur en chef : c’est lui qui peut publier, dépublier ou détruire un document.
La principale tâche de l’éditeur consiste à gérer la publication dont il a la charge. Il doit entre autres décider de l’opportunité de publier ou non un document. Publier un document dans Lodel signifie le rendre visible sur l’interface publique (à n’importe quel internaute).

Quelques remarques préalables :

par défaut, tout document chargé dans Lodel se voit attribuer le statut « prêt à publier »
Si l’utilisateur qui dispose d’un niveau rédacteur peut charger des documents dans l’interface de Lodel, il ne peut les publier. Les documents resteront donc « prêts à publier ». Ils ne seront donc pas visibles par l’internaute, mais seulement par les utilisateurs de Lodel ayant accès à l’interface d’administration du logiciel (le « back-office »).
Tout document chargé par un rédacteur doit donc être validé par un éditeur (ou un utilisateur de rang plus élevé).
Cette séparation des tâches a été améliorée par rapport à la version 0.7 de Lodel. Dans cette version, le rédacteur qui chargeait un document n’y avait plus accès : il ne pouvait donc plus, par exemple, recharger un document déjà chargé – une fonction très utile, car beaucoup d’erreurs (de stylage entre autres) peuvent apparaître sur la page de prévisualisation. Dans la version 0.8, le rédacteur peut recharger les documents qu’il a chargés, et récupérer les fichiers source.

Gérer la structure du site (à compléter)
----------------------------------------

Présentation générale
---------------------

La page racine de votre site permet:

de créer la structuration de votr esite en créant des publications emboîtées (on parle également d’arborescence).
d’ajouter des documents à des publications, situées à divers niveaux de l’arborescence. Ces documents peuvent être de différents types selon le modèle éditorial adopté.
Les menus déroulants « ajouter… » permettent d’ajouter des publications ou des documents, ils ouvrent, selon le cas, la fenêtre de création d’une publication, la fenêtre de saisie d’un document ou la fenêtre d’importation d’un document.

Mise en place de l’arborescence du site
---------------------------------------

1ère étape : penser l’arborescence
----------------------------------

Avant d’entreprendre la réalisation d’un site, il convient de penser l’arborescence du site. Selon le type de modèle éditorial choisi, divers types de publications et de documents sont proposés. Il s’agit avant tout de penser la hiérarchie des publications avant de les créer.

Les deux entités essenielles du site sont le document et la publication.

Les documents constituent le contenu principal du site : articles d’une revue, communications d’un colloque, billets d’un blog, comptes rendus, notes de lecture…
Les publications contiennent les documents : les numéros d’une revue, les journées d’un colloque, les rubriques d’un blog…
Pourquoi plusieurs types de documents ?

Les types de documents permettent de distinguer les documents entre eux, de leur faire subir des traitements différents, et de leur affecter une mise en forme (template) adaptée. En effet, à chaque type de document est associé un template, c’est-à-dire un modèle graphique de document. Ainsi, les articles peuvent avoir une mise en forme différente des comptes rendus, etc. les types de documents sont également utilisés dans les sommaires ou dans les index, pour classer les documents.
Les types de documents font partie du modèle éditorial. Si vous souhaitez les modifier, il faut disposer des droits d’administrateur Lodel

2e étape : créer l’arborescence
-------------------------------

Dans la page « racine du site », cliquez sur le type de publication à créer (dans le menu déroulant). S’ouvre alors une page d’édition des métadonnées. Celle-ci vous rappelle sans doute la page d’édition des métadonnées d’un document, c’est normal : il s’agit de la même page, à quelques particularités près, comme le bloc de gestion des publications :

Remplissez les champs (titre, langue, date de publication, icône, titre alternatif dans une autre langue, etc.), en suivant les consignes affichées. Validez. La publication s’affiche alors sur la page « racine du site ».

Si vous souhaitez créer une sous-publication, il faut se placer à l’intérieur de celle-ci. Cliquez sur le titre de la publication parente. Grâce au menu déroulant, vous pouvez à nouveau créer une publication, en suivant la même procédure que celle décrite ci-dessus.

Vous pouvez ainsi créer de multiples publications emboîtées. En haut de la page, sous les onglets de navigation, le fil d’ariane vous rappelle la position de la publication créée dans votre arborescence.

Le statut du document
---------------------

Il existe quatre statuts de documents dans Lodel. On distingue :

Statuts non publiés
-------------------

Les documents non publiés ne sont accessibles qu’aux personnes identifiées dans Lodel. Les internautes n’y ont jamais accès.

Brouillon : l’entité n’est pas publiée. Pour la publier, il faut deux actions dans l’interface. La première permet de passer l’entité en « prêt à publier ». La seconde, de la publier. Ce statut crée donc une protection, qui permet d’éviter toute publication intempestive d’un document sur lequel il reste du travail.
Prêt à publier : le document ou la publication n’est pas visible par l’internaute lorsqu’il navigue sur le site. En revanche, l’utilisateur de Lodel connecté peut voir le document et, si son statut le lui permet, le travailler, le modifier.

Statuts publiés
---------------

Seuls les documents publiés sont visibles par l’internaute sur le site.

Publié : dans ce cas, le document est visible par l’internaute sur le site
Protégé : ce statut est un niveau supplémentaire, qui permet de sécuriser le processus de publication, en rendant difficile sa dépublication. Pour la dépublier, il faut deux actions dans l’interface.
Attention : la dépublication est une action importante qu’il ne faut pas effectuer à la légère. Lorsqu’un document a été publié, il est visible sur un site, un visiteur peut donc le voir, le citer, ou conserver l’adresse pour son usage personnel. La dépublication de cette page la rendra inaccessible pour l’internaute : même si le document est republié, l’URL sera changée. Cela rompra donc la chaîne hypertextuelle, et contredira le principe de citabilité. La dépublication est donc possible techniquement, mais déconseillée d’un point de vue éditorial. Pour corriger un document, il est préférable d’utiliser la fonction « recharger un document ».

Les icônes associées aux statuts
--------------------------------

A chaque statut de document correspond une icône qui apparaît à côté du titre du document dans la publication.

(Le texte intégral n’est pas disponible pour l’internaute, mais sera publié lorsque la date définie par l’utilisateur sera arrivée à échéance. L’ensemble de ses métadonnées, en revanche, sera publié). Il est donc possible de charger dans Lodel un document qui ne sera visible par l’internaute que plusieurs mois après. Il suffit pour cela de modifier la date de publication dans Lodel (qui par défaut, considère que la date de chargement est la date de publication). Voir le tutoriel sur Lodel.org

Changer le statut d’un document
-------------------------------

Par défaut, tout nouveau document a comme statut « prêt à publier ». Une fois la relecture effectuée, cliquez sur le bouton « Publier », à droite du titre de votre document. Votre document est alors publié. Par contre, si ensuite vous voulez le dépublier, Lodel vous demandera confirmation de cette action, pour éviter toute dépublication intempestive.

Les statuts « protégé » et « brouillon » représentent un niveau supplémentaire de sécurité. On n’y accède pas par le même bouton. Pour protéger un document, celui-ci doit déjà être publié. Ensuite, cliquez sur le bouton « éditer ».

« Prêt à publier » et « publié » représentent donc des niveaux de sécurité normaux, tandis que « brouillon » et « verrouillé » garantit une protection supplémentaire contre les manipulations intempestives : « brouillon » est la version protégée de « prêt à publier », « verrouillé » la version protégée de « publié ».

Les fonctions avancées des documents
------------------------------------

Aperçu général
--------------

Voyons à présent les fonctions avancées d’édition des documents permises par Lodel.

Lorsqu’un document a été mis en ligne ou qu’une publication a été créée, on peut traiter ces données présentes sur Lodel.

Changer l’ordre : les flèches verticales de changement d’ordre permettent de déplacer d’un cran la publication ou le document auquel elles correspondent. Cliquez sur la flèche du haut pour remonter d’un cran, sur celle du bas pour descendre d’un cran. Vous pouvez ainsi faire évoluer simplement lordre d’apparition sur le site web des entités concernées.
Voir : cette fonction permet de prévisualiser le fichier mis en ligne tel que le verra l’internaute. On peut ainsi se rendre comptte de la qualité de l’importation et corriger certaines erreurs avant une publivation définitive. Le double fil d’ariane reste présent en haut de la page, ce qui permet de revenir rapidement aux foncitons d’édition du document, en revenant à la publication parente, ou en cliquant sur les boutons d’édition.
éditer » permet d’accéder à la page de métadonnées d’un document ou d’une publication. Vous pouvez modifier les métadonnées du document, attacher une icône, joindre un document annexe, etc. (voir ci-dessous).
« publier/dépublier » : ce bouton permet de changer le statut du document
« supprimer » permet de détruire définitivement un document ou une publication de Lodel. Une confirmation est demandée par Lodel. La destruction est définitive.
Attention : cette action est à utiliser avec la plus grande prudence, et n’est accessible qu’au niveau éditeur pour la suppression des documents, et administrateurs pour la suppression des publications. Si vous décidez de détruire un document pour ensuite le republier, sachez que son URL va changer et que sa citabilité en sera donc mieux atteinte, l’utilisation de la fonction « recharger » est alors mieux adaptée. Cette fonction permet de corriger un document mis en ligne sans briser la continuité de la publication. Il n’est en effet pas nécessaire de dépublier un document pour le corriger ou le mettre à jour.

La page éditer
--------------

Cette page permet, comme on l’a vu au niveau visiteur, de très nombreuses actions sur le document ou la publication.

La page d’édition des métadonnées : vue d’ensemble

Prenons-là de haut en bas, en commençant par la colonne de gauche. Cette colonne (dans le cas du modèle éditorial de Revues.org) :

Affiche le titre, sous-titre, titre traduit (champ éditable)
Affiche le résumé (mais le champ n’est pas éditable)
Affiche le début du texte (non éditable), pour mémoire
Permet d’associer un fichier PDF, afin de joindre un fac-similé.
Permet d’éditer des métadonnées (date de publication, langue)
Les entrées d’index sont perfectionnées. On peut rajouter des entrées d’index à partir de l’ensemble des entrées disponibles, ou en supprimer ; il suffit de la sélectionner avec le curseur, et de cliquer sur le bouton du dessus pour l’ajouter aux entrées choisies, celui du dessous pour l’effacer des entrées choisies.
Les entrées d’index

Grâce aux boutons « Ajouter » et « Modifier », on peut ajouter des entrées non présentes dans la liste des entrées disponibles.
Le champ d’édition de l’auteur est plus complexe, et permet d’ajouter de nombreuses informations.
On peut également ajouter des champs « traducteur du document » et « éditeur scientifique ».
Enfin, « Terminer » renvoie au côté édition, tandis que « terminer et visualiser » renvoie côté site.
Toujours dans cette page d’édition du document, on passe à la colonne de droite.

Le bloc « Information sur l’entité » permet, grâce au menu déroulant, de modifier le type du document (éditorial, note de lecture…), mais dans la limite de la cohérence du Modèle Editorial : un article ne peut être transformé en rubrique. Par contre, une rubrique peut devenir un numéro. Cette modification n’était pas possible dans la version 0.7 de Lodel. Il est à présent possible de transformer un éditorial en article, par exemple, sans avoir à détruire le document d’origine (ce qui obérait gravement sa citabilité). Le « Permalien » permet de connaître, à l’avance, l’URL finale du document. En cliquant sur « permalien », une fenêtre pop-up s’ouvre, et affiche l’URL générée par Lodel. Les dates de création/modification sont générées automatiquement par Lodel ; on ne peut donc les modifier manuellement. Attention : il ne faut pas confondre ces dates avec la date de publication qui, elle, est modifiable. Ce champ se situe dans la colonne de gauche de la page d’édition des métadonnées.

Il est possible, juste en dessous, de modifier le statut d’un document

Lorsqu’on modifie le statut d’un document, la modification opère tout de suite, sans confirmation. Si on a effectué des modifications dans la colonne de gauche de la page d’ « édition des donénes relatives à l’entité » (modification du titre, etc.), il faut valider avant de modifier le statut du document, faute de quoi les modifications seront perdues. Comme dans Lodel 0.7, il est possible de déplacer un document. À présent, il est également possible de déplacer des numéros entiers

Le bloc « documents annexes » permet d’ajouter des documents de diverses natures : commentaire, image, vidéo, son, URL… Il s’agit d’anticiper les besoins des revues dans quelques années.
Si on ajoute une image (ou une vidéo), une page d’édition s’ouvre, qui permet de saisir le titre de l’image, de la télécharger, puis de la décrire dans un petit éditeur en WYSIWYG. Par défaut, Lodel génèrera une vignette, mais on peut la générer soit-même, afin, par exemple, de recadrer une image plutôt que de laisser le redimensionnement automatique, qui peut rendre la vignette complètement illisible.

Une fois que le document annexe est ajouté, un trombone sous le titre du document parent :

En cliquant sur le trombone, on revient à la page d’édition du document annexe. Lorsqu’il y a plusieurs documents annexes attachés à un document, il y a autant de trombones que de documents annexes. L’interface est volontairement sommaire à ce niveau : pour ne pas l’alourdir, Lodel 0.8 n’affiche pas les titres des documents annexes. Il faut donc laisser sa souris quelques instants au-dessus du trombone pour savoir quel trombone renvoie à quel document.

Changer le type d’un document
-----------------------------

Lodel permet à présent de modifier le type d’un document ou d’une rubrique directement depuis la page d’édition. Dans le bloc « Informations sur l’entité », cliquez sur le menu déroulant « type », et choisissez le type de l’entité que vous souhaitez modifier. Il n’y a pas de demande de confirmation pour cette action. Il faut cependant valider votre action en cliquant sur « terminer » en bas de la page.

Cette action n’est possible que dans les limites du respect du Modèle éditorial (ME). Un article peut devenir éditorial, mais pas collection, par exemple. Pour en savoir plus sur le ME, reportez-vous à la section ME de la documentation.

Déplacer un document
--------------------

Cette option permet de déplacer un document d’une publication à une autre.

Cliquer sur « déplacer ». la page de déplacement d’un document s’ouvre, afin de sélectionner la destination du document. Sont affichées sur cette page toutes les publications du site, hiérarchisées en fonction de l’arborescence. En orange sont indiquées les rubriques (collections, numéros…) qui sont cliquables, et dans lesquelles vous pouvez déplacer votre document. En gris sont indiqués les niveaux de l’arborescence qui ne sont pas cliquables, et dans lesquels vous ne pouvez déplacer votre document, car il s’agit d’un niveau de hiérarchie inférieure ou égale.

Attention : vous ne pouvez déplacer votre document, ou votre rubrique, que vers un niveau supérieur, un conteneur de votre document ou votre rubrique. Ainsi, vous ne pourrez déplacer une rubrique vers un document, mais vous pourrez le faire vers la racine. De même, vous ne pourrez déplacer un article vers un document annexe, ou un autre article, mais vous pourrez le déplacer vers une rubrique, une collection, ou la racine. Enfin, vous pourrez déplacer un document annexe n’importe quel article, mais pas vers des rubriques ou des collections, afin de respecter la cohérence du modèle éditorial : si vous déplaceiez un document annexe vers une rubrique, le type de document serait radicalement changé.

Cliquer sur la publication dans laquelle le document doit être déplacé. Lodel demande alrs une confirmation. Cliquez sur « Confirmer » pour continuer, ou « annuler » pour abandonner le déplacement.

Remarque : l’URL du document ne change pas, et sa citabilité est donc conservée. Seule change sa position dans la structure du site.

Récupérer le fichier source
---------------------------

Cette fonction permet de récupérer sur le disque dur de son ordinateur le fichier mis en ligne sous sa forme Word, RTF ou SXW, selon les cas.

Grâce à cela, il est possible de récupérer un fichier perdu, de corriger, ou modifier la version la plus récente d’un document mis en ligne, et de manipuler à distance un même document entre plusieurs utilisateurs.

Cliquez sur « récupérer le fichier source ». une fenêtre s’ouvre et propose d’ouvrir le fichier ou ed le télécharger sur le disque dur de votre ordinateur. Vous pouvez ensuite modifier le document source sur votre ordinateur, puis le recharger.

Recharger le document
---------------------

Cette fonction permet de modifier un document en ligne, en réimportant le document depuis le disque dur de votre ordinateur.

Grâce à cela il est possible de corriger un document mis en ligne sans briser la continuité de la publication. il n’est pas nécessaire de dépublier un document pour le corriger ou le mettre à jour.

Cliquez sur « recharger le document ». la page « importation d’un fichier stylé » apparaît. Suivez les étapes de la mise en ligne, identiques à celle de la première importation d’un document.

Gestion des documents annexes
-----------------------------

Il existe 5 types de documents annexes, organisés en trois menus déroulants :

textes simples : commentaires de documents
fichiers : image, vidéo, document sonore ou fichier autre (PDF, etc.)
sites : lien placé en annexe.
Sélectionnez grâce au menu déroulant le type de document annexe voulu. Une page d’édition du document annexe apparaît.

Remplissez les champs associés au document annexe. Indiquez le titre, et chargez le fichier en cliquant sur « parcourir ». Puis validez en cliquant sur « terminer ».

Attention : comme pour tout document ajouté, un fichier annexe chargé dans Lodel est par défaut « prêt à publier ». Votre fichier n’apparaîtra donc pas aux yeux des internautes que si vous le publiez.

Pour cela, retournez dans la page d’édition du document parent. Le document annexe est indiqué par un trombone, ainsi que les actions classiques sur tout document (déplacer, publier, détruire). Publiez votre fichier annexe. L’icône représentant le trombone devient verte, le fichier annexe est alors publié.

Gestion du XML
--------------

Ce bloc permet de manipuler le document au format XML.

Visualiser le XML : permet de voir le XML. Le comportement dépend du type de navigateur que vous utilisez.
Récupérer le fichier XML : permet de déposer le fichier XML sur votre disque dur. Il existe par ailleurs une foncionnalité de sauvegarde de la totalité des fichiers XML dans la zone administration.
Valider le XML : permet de lancer une validation du XML afin de vous assurer de sa conformité aux normes. Aucun fichier ne doit produire d’erreur. Si une erreur survenait lors de la validation, signalez-le à l’équipe de développement de Lodel.
