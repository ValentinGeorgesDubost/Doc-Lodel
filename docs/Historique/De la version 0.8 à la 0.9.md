Seuls quelques modifications dans la base de données sont à effectuer, ainsi que l’ajout de deux paramètres dans le lodelconfig.php.

Également, il vous faudra ajuster vos fichiers de configurations (lodelconfig.php ET siteconfig.php) en suivant les fichiers de configuration de la distribution (respectivement /lodel-0.9/install/plateform/lodelconfig-default.php et lodel-0.9/src/siteconfig.php (ou siteconfigroot.php si vous avez installé Lodel en mode mono-site)).

Voici la marche à suivre pour la base de données générale de Lodel :

- Dans la table urlstack, ajouter un champ ‘site’ : ALTER TABLE urlstack ADD `site` varchar(64) CHARACTER SET utf8 collate utf8_bin NOT NULL;
- Ajouter la table de la messagerie interne : CREATE TABLE `internal_messaging` (
`id` int(10) unsigned NOT NULL auto_increment,
`idparent` int(10) unsigned NOT NULL,
`iduser` varchar(255) default NULL,
`recipient` longtext NOT NULL,
`recipients` longtext NOT NULL,
`subject` varchar(255) NOT NULL,
`body` longtext NOT NULL,
`incom_date` datetime NOT NULL,
`cond` tinyint(1) NOT NULL default ‘0’,
`status` tinyint(4) NOT NULL default ‘0’,
`upd` timestamp NOT NULL default CURRENT_TIMESTAMP on update CURRENT_TIMESTAMP,
PRIMARY KEY  (`id`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8
- Ajout d’un champ ‘userrights’ dans la table session : ALTER TABLE session ADD `userrights` tinyint(3) unsigned NOT NULL default ‘0’
- Ajout de la table ‘mainplugins’ : CREATE TABLE `mainplugins` (
`id` int(10) unsigned NOT NULL auto_increment,
`name` varchar(64) character set utf8 collate utf8_bin NOT NULL,
`upd` timestamp NOT NULL default CURRENT_TIMESTAMP on update CURRENT_TIMESTAMP,
`status` tinyint(4) NOT NULL default ‘0’,
`trigger_preedit` tinyint(1) NOT NULL default ‘0’,
`trigger_postedit` tinyint(1) NOT NULL default ‘0’,
`trigger_prelogin` tinyint(1) NOT NULL default ‘0’,
`trigger_postlogin` tinyint(1) NOT NULL default ‘0’,
`trigger_preauth` tinyint(1) NOT NULL default ‘0’,
`trigger_postauth` tinyint(1) NOT NULL default ‘0’,
`trigger_preview` tinyint(1) NOT NULL default ‘0’,
`trigger_postview` tinyint(1) NOT NULL default ‘0’,
`config` longtext NOT NULL,
`hooktype` varchar(5) NOT NULL,
`title` text NOT NULL,
`description` longtext NOT NULL,
PRIMARY KEY  (`id`),
UNIQUE KEY `name` (`name`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8

À partir de là, il faut, pour chaque site :

- Ajouter le champ ‘ip’ dans la table restricted_users : ALTER TABLE restricted_users ADD `ip` longtext NOT NULL;
- Ajouter la table des plugins : CREATE TABLE plugins (
`id` int(10) unsigned NOT NULL default ‘0′,
`name` varchar(64) character set utf8 collate utf8_bin NOT NULL,
`upd` timestamp NOT NULL default CURRENT_TIMESTAMP on update CURRENT_TIMESTAMP,
`status` tinyint(4) NOT NULL default ‘0′,
`config` longtext NOT NULL,
PRIMARY KEY  (`id`),
UNIQUE KEY `name` (`name`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8;
Il suffit maintenant d’ajouter, dans le lodelconfig.php, les deux paramètres suivants :
$cfg[‘dbDriver’]=’mysql’; // mettre mysqli si votre installation vous le permet
$cfg[‘$sqlCacheTime’]=3600*24; // temps de cache des requêtes SQL, mettre à 0 pour désactiver.

Voilà, votre installation est prête, vous pouvez maintenant télécharger Lodel 0.9, décompresser l’archive, et remplacer les répertoires lodel-0.8, lodeladmin-0.8 et share-0.8 par leurs équivalents 0.9.
