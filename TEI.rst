***Schema TEI OpenEdition***

Ce projet versionne le schéma TEI utilisé sur les plateformes d'OpenEdition Revues.org et OpenEdition Books.
Il correspond au modèle éditorial revuesorg distribué avec Lodel https://github.com/OpenEdition/lodel

Parmi les standards d'encodage XML d'un texte, TEI ([Text Encoding Initiative](<http://www.tei-c.org/>)) est sans doute le plus complet et le plus mûr. TEI définie plus de 500 composants textuels et concepts différents (mots, phrases, caractère, symbole, personne, etc.). Une utilisation personalisée d'un schéma TEI implique une customisation du schéma à ses spécificités, pour s'adapter et réduire la richesse de TEI au schéma restreint (donc simplifié) voulu. La communauté TEI a crée un langage de spécification nommé ODD [("One Document Does it all")](http://www.tei-c.org/Guidelines/Customization/odds.xml) pour modifier le schéma TEI générique. Avec une description ODD, il est possible grâce à un outil nommé Roma de générer de manière automatique des schémas TEI customisés (xsd, relaxNG, etc.) et de la documentation.
Dans ce projet, le dossier odd contiens la description ODD, et le dossier xsd contiens le schéma xsd généré par roma.

Pour valider un fichier XML avec ce schéma, il est possible d'utiliser le schéma en local ou d'utiliser le schéma xsd publié à l'adresse http://lodel.org/ns (se reporter au répertoire /doc pour un exemple de déclaration du schéma dans le fichier xml).

Se reporter aux releases (https://github.com/OpenEdition/tei.openedition/releases) pour connaitre les évolutions du schéma.

Les recommandations d'usage sont décrites avec des exemples dans le wiki du projet (https://github.com/OpenEdition/tei.openedition/wiki)
