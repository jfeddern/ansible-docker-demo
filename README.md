# ansible-docker-demo

## Beschreibung Ansible

Ansible ist ein Configuration Management Tool, welches haupts?chlich zur Automatisierung der Infrastruktur verwendet wird.
Dabei wird der Ansatz "Infrastructure as Code" verfolgt.
Mit Hilfe einer einfachen Syntax in Form von yml-Dateien ist der 'Code' einfach zu lesen und zu verstehen.

Ansible ist ein OpenSource-Projekt. Somit sind bei Nutzung keine Lizenzkosten zu beachten.
Ansible und die verschiedenen Module, die existieren, wurden in Python implementiert.

Um verschiedene Arten von Maschinen Remote zu verwalten, wird beim Ausf?hren eines Ansible-Playbooks eine SSH-Verbindung zur Remote-Maschine erstellt.
Nachdem das Ansible-Playbook durchgef?hrt wurde, wird die Verbindung wieder geschlossen.

### Ansible-Installation

Hier am Besten einer der zahlreichen Anleitungen im Internet folgen:

- http://docs.ansible.com/ansible/latest/intro_installation.html#latest-releases-via-apt-ubuntu
- https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-ansible-on-ubuntu-14-04

Wichtig hierbei ist, dass alle Remote-Maschinen, die durch Ansible verwaltet/konfiguriert werden sollen, den Public-Key des Ansible-Hosts ben?tigen.

### Ansible Aufbau der Skripte

Im Grunde gibt es drei Hauptkomponenten in Ansible, die notwendig sind.

- Playbooks
- Inventory
- Roles

#### Playbooks

Playbooks sind die steuernde Komponente in Ansible.
Um VMs remote zu verwalten, muss ein Playbook geschrieben werden, welches definiert auf welchen VMs, welche Rollen ausgef?hrt werden sollen.

Mehr Informationen in der Online-Dokumentation unter:

- http://docs.ansible.com/ansible/latest/playbooks.html
- http://docs.ansible.com/ansible/latest/playbooks_special_topics.html


#### Inventory

Das Inventory (oder auch Hostfile genannt) existiert in Form einer yml-Datei.
Im Inventory werden alle VMs definiert, die durch Ansible verwaltet werden sollen.

Hierbei kann auch eine Gruppierung der VMs ?ber eine bestimmte Notation [groupname] vorgenommen werden.
Dies ist z.B. dann hilfreich, wenn virtuelle Maschinen eines unterschiedlichen Typs verwaltet werden sollen.
Klassisches Beispiel f?r eine Gruppierung, ist die Aufteilung in Gruppen f?r Datenbank- und Webserver.

Im Normalfall wird die IP-Adresse und/oder der Hostname der zu verwaltenden Maschine im Inventory eingetragen.

Mehr Informationen in der Online-Dokumentation unter:

- http://docs.ansible.com/ansible/latest/intro_inventory.html


#### Roles

Die Realisierung von Rollen f?hrt zu einer wesentlich besseren Strukturierung bzw. einem besseren Aufbau der Ansible-Skripte.
In Rollen werden die Befehle definiert, die auf den Remote-Maschinen ausgef?hrt werden sollen.
Innerhalb eines Playbooks wird definiert welche Rolle letztendlich ausgef?hrt werden soll.
Eine Rolle kann in mehreren Playbooks verwendet werden.
Es macht also Sinn sich vor der Realisierung der Ansible-Skripte Gedanken dar?ber zu machen, wie diese in Rollen strukturiert werden sollen.


## Ansible Module

Die Community um Ansible ist in den letzten Jahren stark gewachsen. Dies f?hrt dazu, dass immer mehr Module entwickelt wurden, die f?r das Ausf?hren eines Befehls verwendet werden k?nnen.
Gibt es jedoch kein Modul, k?nnen Konfigurationen immer noch ?ber eine API des jeweiligen Tools/Produktes oder ?ber die allgemeinen Module "shell" und "command" ausgef?hrt werden.

Mehr Informationen in der Online-Dokumentation unter:

- http://docs.ansible.com/ansible/latest/list_of_all_modules.html

F?r Docker wurden ebenfalls Module entwickelt, die beim Deployment bzw. beim Bauen von Docker-Images unterst?tzen sollen.

- http://docs.ansible.com/ansible/latest/docker_container_module.html#docker-container
- http://docs.ansible.com/ansible/latest/docker_image_module.html#docker-image