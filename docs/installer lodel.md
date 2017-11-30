# Installation de LODEL préinstallé sur une VM  

Pour tester le logiciel, il est recommandé d'installer la version pré-installée disponible à l'adresse suivante : [http://lodel.org/downloads/vms/2017](http://lodel.org/downloads/vms/2017) et suivez les instructions du readme.
(La version 2017 doit être mise à jour -> utilisez pour l'instant [version 2016](http://lodel.org/downloads/vms/2017), plus stable).

Il est cependant bien sûr possible de faire l'installation soi-même (à partir d'un OS Linux ou d'une VM vierge),
voici les étapes à suivre:  

# Installation sur une VM (VirtualBox)   

## Principes d'une installation  
- Cloner de préférence la dernière version tagguée.
- Faire pointer le virtual host sur la racine de l'installation Lodel.
- L'utilisateur du serveur HTTP doit avoir les droits de lecture sur tous les fichiers.
- Créer une base de donnée et un utilisateur ayant les droits de modification sur cette base.
- Aller à l'adresse configurée avec un navigateur web, suivre les instructions dans l'IHM. Il faudra donner temporairement les droits d'écriture sur le dossier d'une instance de site.
- Vérifer qu'à l'intérieur du dossier d'un site l'utilisateur du serveur HTTP (ex. www-data) a bien les droits d'écriture sur les dossiers: upload, docannexe, docannexe/file, docannexe/image, lodel/sources, lodel/icons

## Détail des étapes  
A partir d'une machine virtuelle VirtualBox.
Si vous partez d'une image Debian9 vierge, installer sudo (https://blog.seboss666.info/2014/05/installer-et-utiliser-sudo-sur-debian/) :
`su root`  
`apt-get update`  
`apt-get install sudo`  
Ajoutez vous comme sudoer : ajoutez un fichier (`sudo nano /etc/sudoers.d/votreuser`) contenant 1 ligne:
 `$USER ALL = ALL`
puis rebootez.  

Si besoin, augmenter la taille disque: VBoxmanage modifyhd cheminVM/dd.vdi --resize tailleenMo

### installation des PAQUETS :   

`sudo apt-get update`  
`sudo apt-get dist-upgrade`  

`sudo apt install mysql-server`  
`sudo apt install mysql-client`  
`sudo apt-get install php php-fpm`  (installe php7 sur debian9)  
Pour éviter que apache et nginx n'interfèrent, supprimez apache2 (installé par défaut sur Debian)
`sudo apt-get remove apache2`  (ou`sudo apt-get purge apache2`)    
`sudo apt-get install nginx`  
`sudo apt-get install git`  

Ajouter les dépendances PHP pour Lodel:
`sudo apt-get install php7.0-mbstring php7.0-xml php7.0-gd php7.0-curl php7.0-mysqlnd php7.0-zip` 
Pour vérifier quels modules vous avez installés:
`dpkg --list|grep php` 
Pour vérifier si ils sont bien pris en compte par PHP-FPM:
`sudo /usr/sbin/php-fpm7.0 -m`  
Cf. plus loin, lodeladmin/install.php vérifie que les modules sont disponibles pour Lodel.

### Config MYSQL  

- cf. https://doc.ubuntu-fr.org/mysql :
<pre><code>mysql -u root -p
create user 'nom_utilisateur'@'localhost' identified by 'votremdp';
GRANT ALL PRIVILEGES ON *.* TO 'nom_utilisateur'@'localhost';</code></pre>

- changement du mot de passe du root sur la base :
<pre><code>	su root
	mysql -u root
	USE mysql
	UPDATE user SET Password=PASSWORD('votremdp') where User='root';</code></pre>

- Si un problème survient avec le mot de passe de mysql, cf. https://dev.mysql.com/doc/refman/5.7/en/resetting-permissions.html
- Pour vérifier si MySQL est lancé :
	`sudo service mysql status` 

### Config PHP    
 
- Editer php.ini (`sudo nano /etc/php/7.0/fpm/php.ini`) et faire `cgi.fix_pathinfo = 0`(décommenter la ligne)  
- La conf de PHP est dans dans `/etc/php/7.0/fpm/` (notamment php-fpm.conf et dans pool.d/www.conf qui définit le pool de connexions à FPM (qui écoutent sur /var/run/php/php7.0-fpm.sock) et qui précise que l'utilisateur FPM est user:www-data/group:www-data); le processus est dans /var/run/php/php7.0-fpm.pid; le log est dans /var/log/php7.0-fpm.log;

- vérifier si php-fpm est lancé :
	`sudo service php7.0-fpm status`  
- pour relancer PHP-FPM
        `sudo service php7.0-fpm restart`  
	
### config NGINX   

Pour en savoir plus sur la config, cf. [le wiki de Nginx](https://www.nginx.com/resources/wiki/start/topics/examples/phpfcgi/). 

La config de nginx est dans /etc/nginx.
le fichier principal est nginx.conf ; la définition de la configuration du site lodel s'ajoute dans le répertoire sites-available et comme lien symbolique.

On vous propose ici une configuration basique pour remplacer le fichier conf.
`sudo mv nginx.conf nginx.conf.old` puis créez un fichier nginx.conf avec cette configuration.
et ajoutez un fichier lodel dans le répertoire sites-available
puis un lien symbolique depuis sites-enabled : `sudo ln -s /etc/nginx/sites-available/lodel /etc/nginx/sites-enabled/lodel`

- puis relancez PHP-FPM
        `sudo service nginx reload`   
- pour vérifier si php-fpm est lancé :
	`sudo service nginx status` 

### Création et config de l'instance LODEL  

Suivre les instructions de https://github.com/OpenEdition/lodel/blob/master/INSTALL :
`git clone https://github.com/openedition/lodel`  
(au besoin: `git checkout la_branche_qui_vous_intéresse` )

Ensuite:
<pre><code>
cp lodelconfig-default.php lodelconfig.php
grep install_key lodelconfig.php
touch 03dde1bd-c6b6-4424-8618-c4488e30484a
`#passer root (su root)`
mysql -u root -p
`#(pass :votremdp)`
create user 'lodeluser'@'localhost' identified by 'password';
CREATE DATABASE `lodel` CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;
GRANT ALL on `lodel`.* TO lodeluser@localhost identified by "password";
GRANT ALL on *.* TO lodeluser'@localhost identified by "password";
</code></pre>  
puis mettre à jour `lodelconfig.php` avec ces infos (database, dbusername, dbpasswd, dbhost)  
et **commenter la ligne exit;** (avec //)  

Connectez-vous à `127.0.0.1/lodeladmin/install.php` (qui vérifie si toutes les libs php sont installées, entre autres),
puis si tout est Ok, suivez les instructions qui vous invitent à vous connectez en tant que Username: admin / Password: xxxxxxxxxxxxxx,
puis à créer un autre utilisateur avec les droits LodelAdmin, puis à créer un site.
Supprimez ensuite le fichier 03dde1bd-c6b6-4424-8618-c4488e30484a (et aussi l'utilisateur admin initial).  

### Tester l'installation  

Pour se connecter au back-office (Admin lodel):   
http://localhost:9095/lodeladmin
