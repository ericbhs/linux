==========================================
La connexion sécurisée à distance avec SSH
==========================================

* Telnet : non sécurisé (non crypté)
* SSH : ~Telnet crypté

``ssh rico@192.168.1.5``
    se connecte en ssh au login ``rico`` et à la machine d'adresse ip ``192.168.1.5``
	
Se connecter en SSH sans mot de passe avec une paire clé publique/privée (Windows 10)
-------------------------------------------------------------------------------------

https://blogs.endjin.com/2019/09/passwordless-ssh-from-windows-10-to-raspberry-pi/

#. Vérifier que le dossier ``C:\Users\<name>\.ssh`` existe. Aller dans ce répertoire et créer une paire de clés. Il n'est pas nécessaire d'entrer une passphrase.

	``ssh-keygen``

	Une clé publique (.pub) et une clé privés (sans extension) ont été créées.

#. Dans powershell, démarrer le service ``ssh-agent`` :

	``Set-Service ssh-agent -StartupType Automatic``

	``Start-Service ssh-agent``

#. Charger la clé dans ``ssh-agent``

	``ssh-add C:\Users\<name>\.ssh\id_rsa`` (remplacer "id_rsa" par le nom du fichier créé avec ``ssh-keygen``)

#. Copier la clé publique vers la machine Linux

	``scp id_rsa.pub pi@192.168.1.5:~/``

#. Sur la machine Linux, ajouter le contenu de la clé publique dans le fichier ``.ssh/authorized_keys`` (s'il n'existe pas il sera créé)

	``cat id_rsa.pub >> .ssh/authorized_keys``

#. Modifier les droits de ``.ssh/authorized_keys`` (ne semble pas indispensable)

	``chmod 600 .ssh/authorized_keys``


