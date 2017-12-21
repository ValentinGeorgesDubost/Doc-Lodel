Quelques bugs mineurs ont été corrigés depuis la RC1, principalement :

- diverses corrections pour ne pas déclencher d’erreurs E_NOTICE
- débuggage du changement de langue d’un utilisateur de l’accès restreint
- l’idparent n’était plus récupéré lors de l’édition d’une entité : l’action de déplacement d’une entité ne fonctionnait donc plus
- correction de la macro « PRELUDE » de la maquette du modèle éditorial Revues.org
- correction d’un bug à l’import XML d’un modèle éditorial : certains identifiants n’étaient plus uniques
- ajout du filtre lin_array, version LodelScript de la fonction PHP in_array (http://php.net/in_array)
- ajout de la variable de configuration ‘searchEngine’ indiquant si le moteur de recherche interne doit indexer les entités dont le modèle éditorial a été prévu pour (par défaut désactivé)
- correction d’un bug quant à la gestion des champs d’une classe et des masques
- correction du javascript permettant de déployer les entités côté interface

Attention, à partir de cette release, Lodel n’acceptera plus les bases de données ayant un encodage différent de l’utf8, et s’arrêtera instantanément s’il rencontre une base de données dans un autre encodage.

Également, le parser LodelScript n’accepte plus maintenant que des attributs (dans les blocs de conditions ou les boucles) sous la forme attr= »value » (les simples quotes ne sont plus reconnues et leur utilisation provoquera des erreurs).
