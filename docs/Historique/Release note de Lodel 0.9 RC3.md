Et voici très certainement la dernière release candidate avant la sortie finale de la 0.9.

Cette RC corrige des petites erreurs concernant le niveau d’erreur (principalement E_NOTICE), et principalement les bugs suivants :

- bug du parser LodelScript n’incluant plus un fichier de déclaration de filtre sur les résultats SQL d’une LOOP.
- la langue d’un bloc LodelScript ne correspondant plus à la langue de navigation dans le site
- bug dans le controller, qui créait une boucle de redirection infinie lorsqu’on appellait, côté site, une entité n’ayant pas de template associé et se situant à la racine du site
