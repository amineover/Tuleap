# Tuleap Plugins installation :

Tuleap est livré avec beaucoup de plugins, ils apportent de nouvelles fonctionnalités et peuvent être facilement installés et configurés.

## Installer de nouveaux plugins :

#### L'installation se fait en 2 étapes :

* Tout d’abord, vous devez installer le paquet RPM correspondant.
* Ensuite, vous devez installer et activer à partir de l'interface d'administration du site

Lorsque vous souhaitez installer un nouveau plugin, lancez (où tuleap-plugin-awesomestuff est le nom du paquet du plugin que vous souhaitez installer):

      # On RHEL/CentOS 7
      yum install tuleap-plugin-awesomestuff
      /usr/share/tuleap/tools/utils/php73/run.php --module=nginx
      systemctl reload nginx
      systemctl restart tuleap-php-fpm

      # On RHEL/CentOS 6
      yum install tuleap-plugin-awesomestuff
      /usr/share/tuleap/tools/utils/php73/run.php --module=nginx
      service nginx reload
      service php73-php-fpm restart

Une fois le plug-in installé, accédez à la page d'accueil de l'administrateur du site Tuleap et accédez à la page d'administration du plug-in. Vous pouvez maintenant installer et activer le nouveau plug-in à partir de l'onglet 'Pas encore installé' 

# Liste de tous les plugins :

**Gestion de projet:**
---

 * **tracker** : Tuleap flagship, suivez tout ce que vous voulez
 * **graphontrackersv5** : Afficher des graphiques au dessus des trackers
 * **agiledashboard** : Do Scrum et Kanban
 * **cardwall** : Construisez un tableau de cartes au-dessus des trackers ou du tableau de bord Agile
 * **velocity** : affichage du graphique de vélocité dans le tableau de bord agile
 Ce module fait partie de Tuleap Entreprise .
 * **taskboard** : gardez une trace visuelle des tâches à effectuer dans un tableau de tâches, utilisé dans Agile Dashboard.
 Ce module fait partie de Tuleap Entreprise .
 * **testmanagement** : campagnes de tests et traçabilité (ou TTM).
 Ce module fait partie de Tuleap Entreprise .
 * **label** : regrouper et afficher les étiquettes sur le tableau de bord du projet (utile pour suivre les demandes d'extraction)
 Ce module fait partie de Tuleap Entreprise .
 * **crosstracker** : agréger les données sur les suivis, même dans les différents projets (beta)
 Ce module fait partie de Tuleap Entreprise .
 * **timetracking** : fournit un moyen facile de suivre votre temps
 Ce module fait partie de Tuleap Entreprise .
 
**Livraisons de fichiers et documentation :**
---

 * **docman** : Gestion de documents
 * **frs** : Améliorer le système de publication de fichiers avec une meilleure vue des versions et une API REST
 * **mediawiki** : Intégration de la technologie wiki «Wikipedia»
 * **webdav** : Accédez à FRS et à la documentation comme un système de fichiers avec le protocole WebDAV

**Contrôle de source et intégration continue :**
---

 * **svn** : Intégration de Subversion (le noyau SVN est obsolète)
 * **git** : intégration de Git
 * **gitlfs** : Ajout du support de Git Large File Storage (LFS) à l'intégration de Git
 * **pullrequest** : Crée des requêtes de pull sur Git
 * **hudson** : intégration de Jenkins
 * **hudson_git** : intégration de Jenkins pour git
 * **hudson_svn** : intégration de Jenkins pour svn

**Authentification et autorisations :**
---

 * **LDAP** : Intégration avec OpenLDAP comme ou Active Directory
 * **openidconnectclient** : déléguer l'authentification à un serveur compatible OpenId Connect
 * **captcha** : Ajouter un captcha à la page de connexion pour éviter les robots
 * **admindelegation** : Déléguer des subventions d'administration aux utilisateurs réguliers
 * **dynamic_credentials** : fournit un moyen de générer des informations d'identification de courte durée
 Ce module fait partie de Tuleap Entreprise .
 * **project_ownership** : ajoute des informations supplémentaires à un projet, telles que la notion de propriété du projet
 Ce module fait partie de Tuleap Entreprise .
 
**Administration:**
---

 * **archivedeleteditems** : quand quelque chose est supprimé, déplacez-le dans un endroit dédié à des fins d'archivage
 * **statistics** : calcule les stats de la plateforme
 * **prometheus_metrics** : Exposer des statistiques à Prometheus sur l'utilisation de Tuleap
 Ce module fait partie de Tuleap Entreprise .

**Intégrations:**
---

 * **bugzilla_reference** : Intégration avec bugzilla, permet de référencer les bugs de bugzilla (et vice-versa)
 * **botmattermost** : Intégration avec Mattmost et Slack
 * **botmattermost-agiledashboard** : le plus important pour Agile Dashboard
 * **botmattermost-git** : Le plus gros robot pour git
 ---
 
 **Remarque**
      Vous pourriez voir d'autres plugins non listés ici. C'est fait exprès, ces plugins ne sont plus maintenus activement, nous n'encourageons donc pas les gens à les utiliser
 
 
### Plugins obsolètes :

Ces plugins ne sont pas compatibles avec RHEL / CentOS 7

Ces plugins ne doivent pas être installés et conservés uniquement pour des raisons héritées du passé. Ils seront enlevés

 * tracker_encryption
 * graphontrackers
