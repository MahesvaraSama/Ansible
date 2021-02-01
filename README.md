# Projet Ansible

Ce repository sert a versionner les roles d'Ansible [Playbook].

Voici quelques liens utiles :
 * [Ansible](https://docs.ansible.com/ansible/latest/index.html)
 * [Ansible line CMD](https://d3vpasha.wordpress.com/2017/05/28/ansible-en-ligne-de-commande)
 * [Ansible DOC FR](https://iac.goffinet.org/ansible-fondamental)
 

## Pour commencer

### Pré-requis 
ce projet nécessitait D'avoir certaines dépendances au préalable.
Tout d'abord il nous faut évidemment l'element principale de ce projet Ansible, Pour cela voici la commande pour pourvoir télécharger Ansible depuis la ligne de commande :
```shell script
apt intstall python3
apt install ansible
```

### Installation 

Après avoir cloné le repository il faudra sois mettre a chaque commande Ansible le roles_path `--playbook-dir=BASEDIR` soit changer le **role_path** d'Ansible pour qu'il puisse cibler celui-ci. Vous devez aller dans ce fichier `/etc/ansible/ansible.cfg` et Intégrer cette ligne dans ce fichier `inventory = ~/path/ansible/hosts` ansi que `role_path = ~/path/ansible/roles`.
Après cela il n'a plus qu'a détailler vos hosts dans un fichier hosts dans le dossier que vous venez de cibler. 
Voici un exemple de la configuration de ce fichier :
```shell script
[docker]
192.168.122.236

[docker:vars]
ansible_user=root
```
Il faut tester votre connexion entre les slaves Ansible avec cette commande :
```shell script
ansible [name] -m ping
```
dans **[name]** vous pourrez choisir entre un host, un groupe d'host ou tous les hosts avec `all`.
Il n'y a plus qu'a installer python avec Ansible sur les hosts avec cette commande : `ansible [name] -m raw -a "yum install -y python3" --user -k -> (if passwd)` 

## Démarrage

Vous n'avez plus qu'a lancer la commande pour lancer le playbook que vous avex besoin _exemple_ `ansible-playbook playbook-docker.yml`

## Arborescence du projet

* **roles**
    _les playbooks Ansible_  
	* **nom du playbook**
	    * **files**
            _tous les fichiers à copier sur le node_  
        * **templates**
            _tous les fichiers de template Jinja_    
        * **tasks**
            _liste des instructions à exécuter (le fichier main.yml est obligatoire)_
        * **handlers**
            _même chose pour les instructions handlers (le fichier main.yml est obligatoire)_
        * **vars**
            _fichier contenant des déclarations de variables (le fichier main.yml est obligatoire) ; les variables définies ici sont prioritaires par rapport aux variables définies dans l'inventaire_
        * **defaults**
            _valeurs par défaut (le fichier main.yml est obligatoire) avec une priorité moindre_
        * **meta**
            _dépendances du rôle et informations (auteur, licence, plateformes...) sur le rôle (le fichier main.yml est obligatoire)_
* **playbook.yml** 
    _Le fichier qui faut lancer pour lancer les playbooks_
    
##### _**PS : certains dossier peuvent etre supprimer car il n'y en a pas besoin pour le playbook**_
