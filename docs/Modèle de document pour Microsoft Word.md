Modèle Word
===========

Le modèle de document pour Word est disponible sur le dépôt GitHub dans la branche suivante : <https://github.com/OpenEdition/lodel/tree/model-word>.  
Des versions taguées sont également disponible dans le dépôt GitHub : model-word-vXX.  
La dernière version est disponible en téléchargement à l'adresse suivante : 
<https://github.com/OpenEdition/lodel/archive/model-word-v3.1.5.zip>

La version 3 est constituée d'une archive zip qui contient :
------------------------------------------------------------

* le modèle _revuesorg_fr.dot_, qui contient les styles déclarés dans le modèle éditorial de Revues.org distribué avec Lodel (modèle à utiliser par défaut) ;
* le modèle _revuesorg_complet.dot_, qui contient un plus grand nombre de styles (résumés dans des langues supplémentaires, index supplémentaires, etc.). L’utilisation de ce modèle de document nécessite la modification du modèle éditorial dans Lodel ;
* les modèles _macros_revuesorg_win.dot_ et ''macros_revuesorg_mac.dot''. Ces deux modèles contiennent des macros qui permettent d’automatiser certaines corrections de stylage et d’erreurs typographiques (une version pour Windows et une version pour MacOS).
* _documentation_modele_revuesorg.doc_ : la documentation d'installation et d'utilisation des macros

Cette version du modèle de document introduit des macros Word qui permettent d'automatiser la correction et le nettoyage des textes. Ces macros permettent de gagner **beaucoup** de temps dans la préparation des textes. Les macros disponibles à ce jour (20/07/2011) sont les suivantes  : 

Macros de corrections de stylage
--------------------------------

* Supprimer les mises en forme et les styles de caractères locaux dans le corps de texte
* Trier les métadonnées
* Vérifier les paragraphes
* Vérifier les niveaux de titre
* Rendre les liens hypertextes actifs

Macros de corrections typographiques
------------------------------------

* Rétablir les espaces insécables dans le corps de texte
* Remplacer les apostrophes verticales par des apostrophes typographiques
* Supprimer les doubles sauts de paragraphe
* Supprimer les points à la fin des titres
* Remplacer les guillemets droits par des guillemets anglais / Remplacer les guillemets droits par des guillemets français
* Effacer le surlignement
* Inverser les italiques dans la sélection en cours / Inverser les italiques dans tout le document

Macros pour les notes de bas de page
------------------------------------

* Supprimer les mises en forme et les styles de caractères locaux dans les notes de bas de page
* Supprimer les doubles sauts de paragraphe dans les notes de bas de page
* Rétablir les espaces insécables dans les notes de bas de page
* Renumérotation des notes
* Supprimer les points après les numéros de notes

Traitements avancés
-------------------

* Traitement par lot
* Transformer les équations Word en images

Modèle Openoffice
=================

Introduction
------------

Le modèle de document pour OpenOffice ou LibreOffice est disponible sur le dépôt GitHub dans la branche suivante : <https://github.com/OpenEdition/lodel/tree/model-libreoffice>  
Des versions taguées sont également disponible dans le dépôt GitHub : model-libreoffice-vXX.  
La dernière version est disponible en téléchargement à l'adresse suivante : 
<https://github.com/OpenEdition/lodel/archive/model-libreoffice-v1.0.zip>

Ce modèle permet d’appliquer les styles déclarés dans le modèle éditorial distribué avec la version 0.8, 0.9 et 1.0 de Lodel. Il fonctionne sous OpenOffice 3.x et LibreOffice 3.x.

Les évolutions de ce modèle seront annoncées sur le blog de Lodel : <http://blog.lodel.org>

L’archive zip contient 3 fichiers :

* modele_revuesorg_fr.ott : le modèle de document
* raccourcis_modele_revorg_fr.cfg : le fichier de configuration des raccourcis claviers permettant d’appliquer les styles au document.
* readme.txt

Installation
------------

* Dans LibreOffice writter, vérifier le niveau de sécurité pour l’exécution des macros :  menu Outils > Options > Libreoffice.org > Sécurité > Sécurité des macros > choisir “Niveau de sécurité moyen”.
* Un double clic sur modele_revuesorg_fr.ott ouvre un nouveau document basé sur le modèle (autoriser l’exécution des macros, bien-sûr).
* Le menu ”Lodel” disponible dans la barre des menus permet d’appliquer les styles déclarés dans Lodel.
* Pour attacher les raccourcis claviers permettant d’appliquer les styles : menu Outils > Personnaliser > Clavier > Charger : choisir le fichier “raccourcis_modele_revorg_fr.cfg” et valider. Les raccourcis clavier sont alors actifs. Ils sont affichés dans le menu “Lodel” en face des styles correspondants.

Restrictions connues
--------------------

La touche “alt” n’est disponible dans les raccrourcis clavier de LibreOffice que depuis la version 3.2. Pour les versions antérieures, la plupart des raccourcis clavier ne sont pas disponibles.

Importation des documents dans Lodel 0.8 ou 0.9 (ServOO) :
* Les listes à puces sont interprétées par Servoo (Lodel 0.8 et 0.9) comme des listes ordonnées : les listes à puces seront affichées dans Lodel comme des listes numérotées. Les listes à puces sont correctement interprétées par OTX (Lodel 1.x)
* Il faut enregistrer le document au format sxw

Importation des documents dans Lodel 1.x (OTX) :
* Les listes à puces sont correctement interprétées par OTX (Lodel 1.x).
* Tous les formats de fichiers compatibles avec LibreOffice 3 sont reconnus par OTX à l'exception de rtf. Il est cependant préférable d'utiliser le format odt.

Recommandations pour le stylage
-------------------------------

Mises en formes locales
-----------------------

Les mises en formes locales peuvent générer des mises en forme non souhaitées dans le document html produit dans Lodel. Pour les supprimer, utilisez la fonction "Formatage par défaut" (accessible depuis le menu Format, ou Ctrl+M). Elle supprime les mises en forme locales (ou formatage direct)et les styles de caractère mais conserve les styles de paragraphe. Les styles utilisés dans le modèle de document sont presque tous des styles de paragraphe.

Le formatage direct est un formatage que vous appliquez sans utiliser les styles, par exemple :
* lorsque vous spécifiez le style gras en cliquant sur l'icône Gras ;
* lorsque vous modifier la Police en la choisissant dans le cadre Nom de police de la barre de formatage.

Stylage des images :
Dans LibreOffice, les images ne sont pas nécessairement contenues dans un paragraphe distinct. Il faut veiller à insérer un paragraphe stylé en “Standard” ou en “Annexe” et contenant l’ancre de l’image et ancrer l'image comme caractère : options de l'image (double-clic sur l'image) : onglet type : ancrer comme caractère.

Stylage des listes :
Importation des documents dans Lodel 0.8 ou 0.9 (ServOO)

Les listes doivent être stylées avec le style de paragraphe "puces" disponible dans le modèle de document.

Importation des documents dans Lodel 1.x (OTX)

Dans Lodel 1.0, il ne faut plus utiliser le style "puces". Il faut utiliser les outils de liste (à puces et numérotées) "natifs" de LibreOffice.

Personnalisation du modèle
--------------------------

Il est bien-sûr possible d’ajouter d’autres styles correspondant à un autre modèle éditorial.

Le principe de ce modèle de document est le suivant :
* le modèle de document contient des styles de paragraphes dont les noms sont déclarés dans le modèle éditorial de Lodel ;
* le modèle contient des macros qui appliquent ces styles (un macro, très simple, par style) ;
* le modèle contient enfin un menu personnalisé qui permet d’exécuter ces macros.
Les raccourcis clavier permettant d’exécuter les macros ne peuvent être enregistrées dans le modèle. C’est pour cette raison qu’il faut les charger depuis un fichier différent.
Pour ajouter un style pour un autre modèle éditorial au menu Lodel :
* Ouvrez le modèle de document dans LibreOffice 3.2 (veillez à ouvrir le modèle de document, pas un nouveau document basé sur le modèle).
* Ajoutez un style dans le modèle de document (dans la fenêtre “Styles et formatage”).
* Enregistrez une nouvelle macro qui applique ce style : “Outils” > “Macros” > “Enregistrez un macro” puis appliquer le style et cliquez sur “Terminer l’enregistrement” et enregistrez cette macro dans le modèle : modele_revuesorg_fr.ott > Lodel > Module1 en lui donnant si possible un nom explicite.
* Pour ajouter cette macro au menu Lodel : Outils > Personnaliser > Menus. Choisissez le menu “Lodel” ou un de ses sous-menus. Cliquez sur “Ajouter” et sélectionnez la macro que vous venez de créer puis “Fermer” et Validez.
* Enregistrez votre modèle. C’est fait.

Si vous souhaitez associer un raccourci clavier à une macro, vous pouvez suivre ce guide très explicite : <http://wiki.services.openoffice.org/wiki/FR/Documentation/Writer_Guide/Assignation_raccourcis>

La sauvegarde des raccourcis semble ne pas fonctionner dans OpenOffice 3.2 (le fichier produit était vide). Elle fonctionne très bien dans LibreOffice 3.2.


Licence
-------

Ce modèle est distribué en licence GPL 2. Merci de faire état de vos essais, qu’ils soient fructueux ou non, sur la liste lodel-users <https://listes.cru.fr/sympa/info/lodel-users>.
Crédits : Matthieu Heuzé, Jean-François Rivière

