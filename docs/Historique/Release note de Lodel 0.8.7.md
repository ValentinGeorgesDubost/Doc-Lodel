Suite au remplacement du système de cache du logiciel et au cours de la sortie d’une série de mises à jour (release), des bugs ont été découverts et rapidement corrigés depuis la version 0.8.2. Voici donc une version 0.8.7 intégrant les corrections nécessaires. Vous trouverez ci-dessous les principales améliorations et corrections de bugs.

Nouvelles fonctionnalités, améliorations et mises à jour
--------------------------------------------------------

Améliorations logicielles
-------------------------

Visibles par l’utilisateur :
----------------------------

- les options des sites peuvent maintenant être multi-langues
- le renseignement du courriel est désormais obligatoire lors de la création d’un utilisateur
- la page ‘missing.html’ a été ajoutée et s’affiche lors de la demande d’une page qui n’existe pas
- dans le choix de type de fichier permis au téléchargement (upload), le format XML a été ajouté
- pour restreindre les droits aux seuls administrateurs Lodel, la gestion des droits a été modifiée pour :
  - l’export de données,
  - l’import de données,
  - l’import du modèle éditorial

Fonctionnement :
----------------

- remplacement du système de cache par le paquet PEAR Cache_Lite (http://pear.php.net/package/Cache_Lite)
- la variable globale ‘defaultlang’ prend comme valeur les languages disponibles par défaut dans Lodel
- erreur 403 renvoyée lorsque le parser rencontre un problème (fichier absent, erreur LodelScript)
- ajout de caractères UTF-8 dans la fonction ‘makeSortKey’ permettant de générer le sortkey des entrées et des auteurs dans les index (tri alphabétique)
- indentation du code source optimisée
- augmentation de la limite de la taille de fichier chargé par le ServOO à 10Mo
- obligation de passer par le fichier index.php pour récupérer les docannexe (similaire à Lodel 0.7)
- erreur 404 renvoyée lorsqu’une page inconnue est demandée

Améliorations de l’interface
----------------------------

- affichage des index optimisé :
  - découpage et affichage des index par lettre (une page par lettre). La présentation se fait par tranche de 30 entrées par lettre, afin d’éviter un temps de chargement trop long
  - l’affichage du nombre d’entrées se fait par type d’index
- Sortie XML :
  - ajout de l’API GeSHi pour la coloration syntaxique du XML d’une entité
  - création du filtre ‘highlight_code’ permettant de coloriser syntaxiquement un contenu HTML/XML

Sécurité
--------

- protection anti-DOS DOS (déni de service) : pour pouvoir regénérer les fichiers mis en cache (clearcache), il faut maintenant être authentifié

Améliorations LodelScript
-------------------------

- ajout d’une possibilité de trier par idtype dans la boucle LodelScript ‘alphabetSpec’

Correction de bugs
------------------

Au niveau :

De l’interface
--------------

- la page de chargement de document par ServOO a été optimisée suite au débuggage du JavaScript

Du Lodelscript
--------------

- correction du comportement de la boucle LodelScript ‘foreach’ (associée aux tableaux) qui créait une erreur PHP (WARNING) lorsqu’on lui passait en argument une variable représentant un tableau vide ou d’un autre type
- réécriture du filtre paranumber de numérotation des paragraphes

Du logiciel
-----------

- correction d’un bug du parser où les en-têtes d’un fichier template n’étaient plus récupérées (refresh, charset…)
- vérification de l’intégrité des URLs : les URL comme www.monsite.com/index.php?id=12/lodel/edition affichaient une page sans styles CSS ; désormais, une page d’erreur s’affiche.
