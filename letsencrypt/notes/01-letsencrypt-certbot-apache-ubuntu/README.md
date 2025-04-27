
# Gestion du développement sous Ubuntu à partir de Windows

* Ouvrir l'éditeur VSCode sous Windows.
* Démarrer une connexion à distance au serveur Ubuntu sous VSCode.
* Ouvrir le répertoire de projet à distance sous VSCode.
* Editer le projet à distance sous VSCode.

# Gestion des lignes de commandes sous Windows

* Ouvrir un terminal PowerShell sous Windows.
* Lancer les commandes à partir du terminal sous PowerShell.

# Gestion des tests du serveur WEB sous Windows

* Ouvrir le navigateur web Google Chrome sous Windows.
* Accéder à l'adresse du serveur web sous Google Chrome.

# Notes sur les tests du serveur WEB sous Windows

* Affichage de la page par défaut du serveur Apache2 sous Google Chrome
* A faire après l'installation du serveur Apache2
* A faire après la récupération de l'adresse IP du serveur Ubuntu
```sh
http://192.168.1.X
```

# Notes sur les configurations sous Windows

* Configuration de la prévisualisation Markdown sous VSCode
* A faire avant l'édition du fichier (README.md)
```json
{
    "workbench.editorAssociations": {
        "*.md": "vscode.markdown.preview.editor",
    }
}
```

* Configuration d'une connexion SSH sous Windows
* A faire avant la connexion SSH au serveur Ubuntu
* C:/Users/[username]/.ssh/config
```sh
# [nom-connexion]--------------------: hostname
# [nom-serveur-ubuntu]---------------: hostname
# [nom-utilisateur-ubuntu]-----------: username
# [numero-port-ssh-serveur-ubuntu]---: 22 [par-defaut]
Host [nom-connexion]
  HostName [nom-serveur-ubuntu]
  User [nom-utilisateur-ubuntu]
  Port [numero-port-ssh-serveur-ubuntu]
```

* Configuration de l'option X11 Forwarding d'une connexion SSH sous Windows
* A faire avant la connexion SSH au serveur Ubuntu afin de pouvoir afficher des fenêtres
* C:/Users/[username]/.ssh/config
```sh
# [nom-connexion]--------------------: hostname
# [nom-serveur-ubuntu]---------------: hostname
# [nom-utilisateur-ubuntu]-----------: username
# [numero-port-ssh-serveur-ubuntu]---: 22 [par-defaut]
Host [nom-connexion]
  HostName [nom-serveur-ubuntu]
  User [nom-utilisateur-ubuntu]
  Port [numero-port-ssh-serveur-ubuntu]
  ForwardX11 yes
  ForwardX11Trusted yes
```

* Configuration de l'option Agent Forwarding d'une connexion SSH sous Windows
* A faire avant la connexion SSH au serveur Ubuntu sans mot de passe malgré une phrase de passe
* C:/Users/[username]/.ssh/config
```sh
# [nom-connexion]--------------------: hostname
# [nom-serveur-ubuntu]---------------: hostname
# [nom-utilisateur-ubuntu]-----------: username
# [numero-port-ssh-serveur-ubuntu]---: 22 [par-defaut]
Host [nom-connexion]
  HostName [nom-serveur-ubuntu]
  User [nom-utilisateur-ubuntu]
  Port [numero-port-ssh-serveur-ubuntu]
  ForwardX11 yes
  ForwardX11Trusted yes
  ForwardAgent yes
```

# Notes sur les configurations sous Ubuntu

* Configuration du port du serveur Apache2
* A faire avant de lancer le serveur Apache2
* /etc/apache2/ports.conf
```sh
# Listen [numero-port-serveur-web-ubuntu]
  Listen 5555
```

* Configuration du répertoire racine du serveur Apache2
* A faire avant de lancer le serveur Apache2
* /etc/apache2/sites-available/000-default.conf
```
```

# Notes sur les commandes sous Ubuntu

* Commande de mise à jour du système Ubuntu
* A faire avant chaque installation d'un nouveau package
```sh
sudo apt update
sudo apt upgrade -y
```

* Commande d'installation du serveur apache2
* A faire avant la mise en oeuvre du serveur Apache2
```sh
sudo apt install apache2 -y
```

* Commande de redémarrage du serveur Apache2
* A faire après chaque modification des fichiers de configurations du serveur Apache2
```sh
sudo systemctl restart apache2
```

* Commande d'affichage du status du serveur Apache2
* A faire pour toute vérification de l'état du serveur Apache2
```sh
sudo stystemctl status apache2
```

* Commande de récupération de l'adresse IP du serveur Ubuntu
* A faire avant d'accéder à la page du serveur à partir du navigateur WEB
```sh
ip a s
```

* Commande d'affichage du propriétaire et du groupe d'un fichier
* A faire avant la modification du propriétaire et du groupe d'un fichier
* Notez le nom du propriétaire et du groupe du fichier [user]:[group]
```sh
# -rw-r--r-- 1 [user] [group]  275 Apr 25 15:30 [nom-fichier]
  -rw-r--r-- 1 root   root     275 Apr 25 15:30 /etc/apache2/ports.conf
```

* Commande de modification du propriétaire et du groupe d'un fichier
* A faire avant la modification d'un fichier [root] sous VSCode
```sh
# sudo chown -R [user]:[group] [nom-fichier]
  sudo chown -R $USER:$USER    /etc/apache2/ports.conf
```

* Commande de modification du propriétaire et du groupe d'un fichier
* A faire après la modification d'un fichier [root] sous VSCode
```sh
# sudo chown -R [user]:[group] [nom-fichier]
  sudo chown -R root:root      /etc/apache2/ports.conf
```

# Notes sur les commandes sous Windows

* Commande de création d'une clé SSH sous Windows
* A faire avant l'automatisation de la connexion de VSCode au serveur Ubuntu
* Cela génère la clé privée (C:/Users/[username]/.ssh/id_ed25519)
* Cela génère la clé publique (C:/Users/[username]/.ssh/id_ed25519.pub)
```sh
# [type-cle]----------: ed25519 | rsa
# [taille-cle]--------: 4096
# [etiquette-cle]-----: youremail@domain.com
ssh-keygen -t [type-cle] -b [taille-cle] -C '[etiquette-cle]'
```

* Commande de copie de la clé publique dans la liste des clés authorisées sous Ubuntu
* A faire avant l'automatisation de la connexion de VSCode au serveur Ubuntu
* Cela ajoute la clé publique au fichier Ubuntu (/home/admins/.ssh/authorized_keys)
```sh
# [nom-fichier-cle-publique-windows]--: ./.ssh/id_ed25519.pub
# [nom-utilisateur-ubuntu]------------: username | root
# [adresse-ip-ubuntu]-----------------: hostname
ssh-copy-id -i [nom-fichier-cle-publique-windows] [nom-utilisateur-ubuntu]@[adresse-ip-ubuntu]
```

* Commande de modification de la phrase de passe  d'une connexion SSH sous Windows
* A faire avant la connexion SSH au serveur Ubuntu sous Windows
* Entrer une phrase de passe vide pour une connexion SSH sans mot de passe
```sh
# ssh-keygen.exe -p -f [nom-fichier-cle-privee-windows]
  ssh-keygen.exe -p -f ~/.ssh/id_ed25519
```

* Commande vérifier l'exécution du service [ssh-agent] sous PowerShell
* A faire avant une connexion SSH sans mot de passe malgré une phrase de passe
```ps
Get-Service ssh-agent
```

* Commande vérifier l'exécution du service [ssh-agent] sous Git Bash
* A faire avant une connexion SSH sans mot de passe malgré une phrase de passe
```sh
echo $SSH_AGENT_PID
```

* Commande de démarrage temporaire du service [ssh-agent] sous PowerShell
* A faire avant une connexion SSH temporaire sans mot de passe malgré une phrase de passe dans le Terminal qui l'utilise
```ps
# Assurez-vous d'être administrateur
Start-Service ssh-agent
```

* Commande de démarrage temporaire du service [ssh-agent] sous Git Bash
* A faire avant une connexion SSH temporaire sans mot de passe malgré une phrase de passe dans le Terminal qui l'utilise
```sh
eval "$(ssh-agent -s)"
```

* Commande de démarrage automatique du service [ssh-agent] sous PowerShell
* A faire avant une connexion SSH permanente sans mot de passe malgré une phrase de passe
```ps
# Assurez-vous d'être administrateur
Set-Service ssh-agent -StartupType Automatic
Start-Service ssh-agent
Get-Service ssh-agent
```

* Commande d'arrêt du service [ssh-agent] sous PowerShell
* A faire pour un'arrêt de la connexion SSH sans mot de passe malgré une phrase de passe
```ps
# Assurez-vous d'être administrateur
Stop-Service ssh-agent
```

* Commande de suppression du service [ssh-agent] sous PowerShell v6
* A faire pour une suppression de la connexion SSH sans mot de passe malgré une phrase de passe
```ps
# Assurez-vous d'être administrateur
Remove-Service -Name "ssh-agent"
```

* Commande d'ajout d'une clé privée au service [ssh-agent] sous Windows
* A faire avant une connexion SSH sans mot de passe malgré une phrase de passe
```sh
# ssh-add [nom-fichier-cle-privee-windows]
  ssh-add ~/.ssh/id_ed25519
```

* Commande d'affichage de la liste des clés SSH gérées par le service [ssh-agent] sous Windows
* A faire pour une connexion SSH sans mot de passe malgré une phrase de passe
```sh
  ssh-add -l
```

* Commande de démarrage d'une connexion SSH sous Windows
* A faire pour la connexion SSH au serveur Ubuntu
```sh
# ssh [nom-utilisateur-ubuntu]@[adresse-ip-ubuntu]
  ssh [username..............]@[hostname.........]
```

* Commande de démarrage d'une connexion SSH avec l'opotion X11 Forwarding sous Windows
* A faire pour la connexion SSH au serveur Ubuntu afin de pouvoir afficher des fenêtres
```sh
# ssh -X [nom-utilisateur-ubuntu]@[adresse-ip-ubuntu]
  ssh -X [username..............]@[hostname.........]
```

* Commande de démarrage d'une connexion SSH avec l'opotion Agent Forwarding sous Windows
* A faire pour la connexion SSH au serveur Ubuntu sans mot de passe malgré une phrase de passe
```sh
# ssh -A [nom-utilisateur-ubuntu]@[adresse-ip-ubuntu]
  ssh -A [username..............]@[hostname.........]
```

# Notes sur les formats de données sous Ubuntu

* Format des clés SSH authorisées sous Ubuntu
* A visualiser après la création/copie d'une nouvelle clé SSH sous Windows
* /home/admins/.ssh/authorized_keys
```sh
# [type-cle-windows]----------------: ssh-ed25519 | ssh-rsa
# [hachage-cle-publique-windows]----: AAAAC3NzaC1lZDI1N...
# [etiquette-cle-windows]-----------: your-email@domain.com
[type-cle] [cle-publique-windows]  [etiquette-cle-windows]
[type-cle] [cle-publique-windows]  [etiquette-cle-windows]
[type-cle] [cle-publique-windows]  [etiquette-cle-windows]
```

* Format des logs d'accès Apache2 sous Ubuntu
* A visualiser après le constat des problèmes d'accès au serveur WEB
* /var/log/apache2/[nom-domaine]_error.log
```sh
[Sat Apr 26 15:53:45.843236 2025] [core:error] [pid 135769] [client 192.168.1.25:51564] AH00037: Symbolic link not allowed or link target not accessible: /var/www/rdvsrv
```
