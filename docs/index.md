Vue d'ensemble de Lodel
=======================

Pour une présentation des fonctionnalités de Lodel, voir la documentation Utilisateur (readthedocs)

**ATTENTION : Doc en construction**.  
Certaines parties datent de la version actuelle de Lodel 0.8.   
De nombreux points sont à revoir.  

Lodel est une application de gestion de contenu web écrit en PHP, fonctionnant avec une base MySQL.
L'application est structurée par son [architecture Modèle Vue Contrôleur](https://doc-lodel.readthedocs.io/en/latest/Architecture%20et%20organisation/ ; reprend l'article <https://lodel.hypotheses.org/configurer/architecture-technique>)

Lodel est un CMS multi-sites:  il y a une base de données par site, un modèle éditorial par site. 

Lodel est conçu pour les besoins de la publication sur le web de contenus scientifiques, revues et livres, et utilise un schéma XML/TEI qui définit cette structure et le type de données.  
Lodel sait nativement traiter des fichiers XML/TEI conformes au schéma Lodel/OpenEdition, et permet aussi d'importer des contenus (article de revue, chapitre de livre) au format Word utilisant des feuilles de style correspondant au schéma TEI, grâce à OTX - autre logiciel libre développé par le Cléo.  

Le modèle éditorial définit, plus largement, tous les contenus gérés par le CMS Lodel (dont les publications scientifiques, mais aussi ); dans Lodel, l'utilisateur peut définir complètement les classes, à partir de 3 types d'objets 'de base': entités, entrées d'index,  personnes.

L'application d'administration est elle-même un site Lodel.  
Le logiciel libre Lodel est publié avec un Modèle Editorial et des templates qui permettent de gérer une site de revue scientifique, mais l'utilisateur peut et doit le plus souvent adapter et compléter pour répondre à ses besoins particuliers.  

Enfin, Lodel est extensible par un mécanisme de plugins.





