# Outils_Observation_Devops
stack Prometheus Grafana Alertmanager
Installation de Stack dans un environnement EC2 Ubuntu
# Mise à jour du système

 ----------------------------------------------------
 
sudo apt-get update
sudo apt-get upgrade
----------------------------------------------------
# Installation des outils nécessaires

 ----------------------------------------------------
 
sudo apt-get install wget curl -y
----------------------------------------------------
# Téléchargement du référentiel

 ----------------------------------------------------
 
wget https://github.com/Allu-Philip/DevOps-Observability.git
----------------------------------------------------
# Prérequis
Avant de commencer l'installation, assurez-vous d'ouvrir les ports suivants pour l'instance EC2 :

----------------------------------------------------

Protocole	Type	Port	CIDR	Description
IPv4	SSH	22	0.0.0.0/0	Accès SSH
IPv4	HTTPS	443	0.0.0.0/0	Accès HTTPS
IPv4	TCP	9100	0.0.0.0/0	Node Exporter
IPv4	TCP	3001	0.0.0.0/0	-
IPv4	TCP	9093	0.0.0.0/0	Alert Manager
IPv4	TCP	9091	0.0.0.0/0	-
IPv4	TCP	3000	0.0.0.0/0	Grafana
IPv4	TCP	9090	0.0.0.0/0	Prometheus
IPv4	TCP	3100	0.0.0.0/0	-
IPv4	TCP	3030	0.0.0.0/0	-
----------------------------------------------------
# Installation de Docker et Docker-Compose
Exécutez le script d'installation de Docker :

 ----------------------------------------------------
 
sh docker.sh
----------------------------------------------------
# Installez Docker-Compose :

----------------------------------------------------

sudo apt-get install -y docker-compose
----------------------------------------------------
# Modifiez les permissions pour Grafana :

 ----------------------------------------------------
chown -R 472:472 grafana
----------------------------------------------------
Modifiez le fichier de configuration par défaut avec l'IP publique de votre instance EC2.

# Exécutez le fichier Docker Compose :

 ----------------------------------------------------
 
docker-compose -f monit.yml up -d
----------------------------------------------------
