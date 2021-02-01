Role Basic
=========

Permet de changer le nom de l'hostname de changer la date + la langue par défaut et installe les paquets utiles sur le serveur pour ainsi permettre d'automatiser les nouveaux serveurs

Requirements
------------

Il ne require rien de spéciale

Role Variables
--------------

Les variables sont sur le default/main.yml

Dependencies
------------

Aucune dépendance n'est requise dans ce role

Example Playbook
----------------

    - hosts: servers
      roles:
         - basic
