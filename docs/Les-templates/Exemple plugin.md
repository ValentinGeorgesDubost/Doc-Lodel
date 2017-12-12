Mon premier plugin dans Lodel
=============================

Nous souhaitons afficher la météo d’une ville choisie, dans l’interface administrateur de notre site lodel bacasable. Un plugin est tout à fait adapté pour réaliser cette nouvelle fonctionnalité. Nous l’appellerons meteo.


Pour démarrer
-------------

Un coup d’œil dans la documentation lodel : http://www.lodel.org/wiki/index.php/Plugins

Premiers pas
------------

Les fichiers de base seront situés dans le répertoire  share/plugins/custom/meteo

Fichier config.xml : au départ, seul le trigger postview est configuré, il permet d’intercepter l’affichage de la page en intégrant l’ajout de la ligne Météo dans la liste des Outils sur la page d’administration du site (onglet Administration).
NB : nous ajoutons dès à présent le trigger preview, même si nous ne l’utilisons pas tout de suite (voir le paragraphe Remarques ci-dessous)

    <?xml version="1.0" encoding="utf-8" ?>
    <LodelPlugin>
    <title>Meteo</title>
    <description>Affichage de la météo</description>
    <sql>0</sql>
    <hookType>class</hookType>
    <triggers>preview,postview</triggers>
    <parameters>
    </parameters>
    </LodelPlugin>

Fichier meteo.php : il contient la définition de la classe meteo, elle-même extension de la classe plugins. Pour ajouter la fonctionnalité Météo dans la liste des actions possibles, il suffit de modifier, avant l’affichage de la page, la liste des fonctionnalités disponibles en ajoutant l’item Météo après l’item Plugins. Météo pointe sur un lien du type ?do=_meteo_list, ce que lodel interprétera comme un appel à la fonction list du plugin meteo.

    <?php
    class meteo extends Plugins
    {
    public function enableAction(&$context, &$error) {}

    public function disableAction(&$context, &$error) {}

    public function preview(&$context) {}

    public function postview (&$context)
       {
        if(!defined('backoffice-admin') || C::get('do') || C::get('lo')
           || ($context['view']['tpl'] != 'index')) return;
        if(!parent::_checkRights(LEVEL_REDACTOR)) { return; }       
        View::$page = preg_replace('/(Plugins</a></li>)/',
           '\1<li><a href="./?do=_meteo_list">Météo</a></li>', View::$page);
       }

    public function listAction (&$context, &$error)
      {
       echo "La météo du jour" ;
       return "_ajax" ;  
      }
    }
    ?>

Il faut maintenant activer ce plugins meteo au niveau de l’installation générale de lodel : le menu Configuration / Plugins permet d’activer le plugin meteo pour tous les sites (ne pas confondre avec installer sur tous les sites). Il faudra ensuite l’activer au niveau du site lodel bacasable (menu Administration / Outils / Plugins).
En rechargeant la page d’administration du site, nous voyons bien apparaître l’item Météo sous le terme Plugins : un clic et La météo du jour s’affiche bien dans l’interface.
Le plus dur est fait, il faut maintenant adapter les scripts et permettre l’affichage personnalisé dans un iframe.

Mise en forme à l’aide d’un template
------------------------------------

nous allons associer à ce plugin un template contenant des lignes au format html, il sera situé dans le sous-répertoire tpl du plugin. Appelons-le meteotpl.html (dans share/plugins/custom/meteo/tpl).

    <html>
     <head>
     <CONTENT VERSION="1.0" LANG="fr" CHARSET="utf-8"/>    
     <TITLE>La météo</TITLE>
      </head>
      <body>
      <h1>La météo du jour</h1>
      </body>
     </html>

La méthode preview doit être modifiée pour associer ce template meteotpl à la classe meteo :

     public function preview (&$context)
     {
     // vérification que l'on est positionné ni dans l'interface d'administration
     // ni dans le template d'affichage de la météo
     if(!defined('backoffice-admin') || $context['view']['tpl'] != 'meteotpl') return;
     // ajout du fichier de template dans la classe qui gère le contexte    
     C::set('view.base_rep.meteotpl', 'meteo');    
     }

La fonction listAction du script meteo.php doit faire appel à ce template meteotpl

     public function listAction (&$context, &$error)
      {
      View::getView()->renderCached('meteotpl') ;
      return "_ajax" ;  
      }
     }

Vider le cache et recharger la page : le titre est maintenant mis en forme
et maintenant, pour terminer, affichage de l’url http://france.meteofrance.com/ dans un iframe : il suffit de modifier le contenu de la balise body dans le fichier template meteotpl.html

     <html>
      <head>
      <CONTENT VERSION="1.0" LANG="fr" CHARSET="utf-8"/>
      <TITLE>La météo</TITLE>
      </head>
      <body>
      <iframe name="stats" SRC="http://france.meteofrance.com/" scrolling="yes"
       height="100%" width="100%" FRAMEBORDER="no"></iframe>
      </body>
     </html>

Encore plus loin : ajout de paramètres
--------------------------------------

Nous souhaitons paramétrer les prévisions en fonction de notre ville de résidence. Tout ceci, uniquement dans l’interface d’administration, sans modification des scripts.
Par exemple, pour Marseille, l’url est de la forme
http://france.meteofrance.com/france/meteo?PREVISIONS_PORTLET.path=previsionsville/130550

Comme nous modifions en profondeur  les caractéristiques du plugin, il faut détruire le plugin dans la table plugins du site bacasable et dans la table mainplugins de l’installation générale.

Modification du fichier config.xml : ajout d’un paramètre ville (par défaut le code correspond à la ville de Marseille).

     <?xml version="1.0" encoding="utf-8" ?>
     <LodelPlugin>
      <title>Meteo</title>
      <description>Affichage de la météo</description>
      <sql>0</sql>
      <hookType>class</hookType>
      <triggers>preview,postview</triggers>
      <parameters>
      <param name="ville" title="Ville" type="text" defaultValue="130550" allowedValues="" required="true"/>
      </parameters>
     </LodelPlugin>

Activation du plugin au niveau de l’installation générale et au niveau du site bacasable.
Modification de la méthode preview pour récupérer la valeur du paramètre ville : il est stocké dans l’attribut _config de l’objet. L’url est construite en tenant compte de cette valeur, elle est stockée dans le contexte C.

     public function preview (&$context)
     {
     if(!defined('backoffice-admin') || $context['view']['tpl'] != 'meteotpl') return;
     C::set('view.base_rep.meteotpl', 'meteo');    
     $ville = $this->_config['ville']['value'] ;
     C::set('urlmeteo', "http://france.meteofrance.com/france/meteo?PREVISIONS_PORTLET.path=previsionsville/".$ville) ;
     }

Modification du template pour intégrer la variable urlmeteo en faisant appel à la variable lodelscript associée [#URLMETEO]

     <html>
      <head>
      <CONTENT VERSION="1.0" LANG="fr" CHARSET="utf-8"/>    
      <TITLE>La météo</TITLE>
      </head>
      <body>
      <iframe name="stats" SRC="[#URLMETEO]" scrolling="yes" height="100%" width="100%" FRAMEBORDER="no"></iframe>
      </body>
     </html>

Exécution !
-----------

Sur la page http://france.meteofrance.com/, nous indiquons la ville qui nous concerne et repérons son identifiant numérique (formulaire Rechercher), par exemple 212310 pour Dijon.
Dans l’interface d’administration du site bacasable, nous sélectionnons le menu Plugins / Configurer correspondant au plugin meteo et nous indiquons la valeur 212310.
Le lien bacasable/lodel/admin/?do=_meteo_list correspondant à l’item Météo affiche bien la météo de la ville de Dijon.

Remarques et astuces
--------------------

Activation du plugin uniquement par l’administrateur lodel

     public function enableAction(&$context, &$error)
          {
          if(!parent::_checkRights(LEVEL_ADMINLODEL)) { return; }
          }

En cas de modification importante du plugin, ajout de trigger par exemple, il faut le détruire directement dans la table mainplugins du serveur lodel et dans la table plugins du site.
en cas d’erreur, vider manuellement le cache : CACHE/triggers
