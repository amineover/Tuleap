# Full Installation

## Pourquoi devrais-je utiliser l'installation complète de Tuleap ?

L’installation complète est le moyen courant d’installer tuleap. Il utilise votre système de paquet de distribution et fournira un environnement entièrement configurable et ajustable. Il est robuste et vous permet de déployer un environnement de production de cette manière.

## Prérequis :

Pour installer Tuleap, vous aurez besoin d’un serveur entièrement dédié. Il peut être virtualisé ou physique. Il n'est pas recommandé d'installer Tuleap sur un serveur hébergeant d'autres applications. Tuleap fournit une suite complète de logiciels et est profondément intégré à son système hôte. L'installation de Tuleap sur un serveur mutualisé posera certainement problème à la fois dans Tuleap et dans vos autres applications.


### Tuleap peut être installé sur les systèmes Linux x86_64 suivants:

	* CentOS ou RedHat 7.x est la plate-forme recommandée.
	* CentOS ou RedHat 6.x sont toujours disponibles, mais déconseillés pour une installation de production. 

* Vous devez désactiver SELinux avant l'installation.
* Le serveur aura besoin d'une connexion Internet car il téléchargera des packages externes.

# Installation :

## Configure les dépendances et télécharge les packages RPM :

Installer EPEL Vous aurez besoin de EPEL pour certaines dépendances:
       yum install -y epel-release
     
Si vous utilisez Red Hat, vous devrez activer le canal facultatif.

## Installer les référentiels de collections de logiciels On CentOS this is done by :
       yum install centos-release-scl

### On RedHat this is done by :
       yum-config-manager --enable rhel-server-rhscl-7-rpms
       
### Install remi-safe repository (needed for PHP dependencies) :
       yum install https://rpms.remirepo.net/enterprise/remi-release-7.rpm
 
### Install Tuleap repositories Create a /etc/yum.repos.d/Tuleap.repo avec ce contenu :  

        [Tuleap]
        name=Tuleap
        baseurl=https://ci.tuleap.net/yum/tuleap/rhel/7/dev/$basearch
        enabled=1
        gpgcheck=1
        gpgkey=https://ci.tuleap.net/yum/tuleap/gpg.key
        
### Install Tuleap en lançant la commande suivante :
 
        yum install -y \
        rh-mysql57-mysql-server \
        tuleap \
        tuleap-plugin-agiledashboard \
        tuleap-plugin-graphontrackers \
        tuleap-theme-burningparrot \
        tuleap-theme-flamingparrot \
        tuleap-plugin-git \
        tuleap-plugin-pullrequest
        
### Configurer la base de données :

Assurez-vous que /etc/opt/rh/rh-mysql57/my.cnf.d/rh-mysql57-mysql-server.cnf contient sql-mode=NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION
Dans la section [mysqld]


     # Add 'sql-mode' parameter after [mysqld]
     sed -i '20 a sql-mode=NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION' /etc/opt/rh/rh-mysql57/my.cnf.d/rh-mysql57-mysql-server.cnf

     # Activate mysql on boot
     systemctl enable rh-mysql57-mysqld

     # Start it
     systemctl start rh-mysql57-mysqld

     # Set a password
     scl enable rh-mysql57 "mysqladmin -u root password"
     
     
# Setup  :

S'il vous plaît ne répétez pas cette étape deux fois. Ce script ne doit être exécuté qu'une seule fois. Si vous rencontrez des erreurs lors des étapes précédentes, veillez à les corriger avant de continuer. En tant que root, lancez:

      /usr/share/tuleap/tools/setup.el7.sh \
      --configure \
      --server-name=FQDN \
      --mysql-server=localhost \
      --mysql-password=XXXXX

#### Avec:

* FQND étant le nom du serveur lorsque vous y accédez sur votre réseau (localhost pour un test local, tuleap.example.com avec une entrée DNS 192.168.1.123 si vous n'avez qu'une adresse IP)

* XXXXX étant le mot de passe du mot de passe root de la base de données configurée précédemment.
  
* Assurez-vous que le pare-feu est correctement configuré. Ouvrir les ports nécessaires:
* Web (TCP / 80 et TCP / 443)
* SSH (git, admin): TCP / 22

# Première connexion :
   
Une fois ces étapes terminées, vous pouvez accéder au serveur Tuleap avec l’interface Web. Accédez à votre nom de domaine Tuleap **(par exemple, https://tuleap.example.com Or https://127.0.0.1) Selon l'adresse de votre serveur .**

Les informations d'identification par défaut de l'administrateur du site se trouvent dans **/root/.tuleap_passwd.** Stockez-le en toute sécurité et supprimez le fichier dès que possible.














 
       
     
