Nouvelles fonctionnalités, améliorations et mises à jour
--------------------------------------------------------

- utilisation désormais possible de plusieurs ServOO (en cas d’interruption momentanée d’un des ServOO)
- possibilité de gérer des accès restreints à certaines pages de l’interface publique (selon la maquette)
- internationalisation : lorsque aucun utilisateur n’est enregistré, la langue du site est prise en compte comme langue -
principale (par défaut) sur l’interface publique
- affichage des index amélioré en interface privée, prenant en compte le type de tri défini dans le ME (hiérarchique, alphabétique, par ordre d’ajout)
- ajout d’un filtre permettant de nettoyer les mises en formes locales sur les appels de notes (cleanCallNotes)
- ajout d’un filtre anti-spam qui crypte les courriels dans la source HTML du document (cryptEmails)
- ajout des classes PEAR Mail et Mail_Mime. Pour leur utilisation, modification de la fonction send_mail qui permet d’envoyer un mail HTML correctement formaté
- ajout d’une White List pour les fichiers qu’il est permis de charger
- ajout d’un champ langue pour préciser la langue des types d’entrées d’index

Corrections de bugs :
---------------------

- résolution du problème des urls de retour aléatoires
- débuggage de la fonction génératrice de textes en différentes langues
- débuggage de l’édition d’une entité : les espaces insécables étaient supprimés des titres lors de l’édition d’une entité (à l’import ou à l’édition)
- lors du rechargement d’un document, le fac-similé est désormais maintenu
- débuggage de la fonction getFileMime qui retournait une information erronée lorsque le nom du fichier comprenait un espace
- modification du filtre isadate pour prendre en compte le fait qu’une date peut être égale à NULL
lors de l’édition par un administrateur d’un utilisateur déjà existant, la double vérification des mots de passe a été désactivée

Développement et optimisation du code LodelScript :
---------------------------------------------------

- ajout des conditions ‘elseif‘ et ‘switch‘
- ajout de la possibilité de comparaison par l’utilisation d’expressions régulières dans une condition
