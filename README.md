# TP_DevOps_Ansible

# S'assurer d'avoir sshpass installé sur son ordinateur
apt install sshpass

# Sur Linux
sudo sysctl -w vm.max_map_count=262144

# Si vous êtes sur windows se connecter à WSL

# Lancer l'installation de Jenkins et Sonarqube (mot de passe become : test)
ansible-playbook -i inventory.ini playbook.yaml -K

# Attendre la fin de l'installation. Soyez patient, cette étape peut demander beaucoup de temps

# S'assurer que Sonarqube est bien operationnel ou sinon attendre qu'il créer la base de donnée
docker logs sonarqube

# Récupérer le mot de passe Jenkins
docker logs jenkins_container

# Finir la configuration de Sonarqube et Jenkins
http://localhost:8080/
http://localhost:9000/

# Ajouter un agent sur la plateforme

# Ajouter un jenkins agent avec Node.JS
docker run -d --network ci-cd --name agent_node -v /var/run/docker.sock:/var/run/docker.sock --init fredericeducentre/jenkins_agent_node -url http://jenkins_container:8080 <secret> <nom_agent_jenkins>

# Vérifier que l'agent s'est bien connecté
docker logs agent_node