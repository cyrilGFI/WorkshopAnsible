# Ansible dans un environnement Windows
Modules Windows :<br/>
https://docs.ansible.com/ansible/latest/modules/list_of_windows_modules.html<br/>

**Exercices:**<br/>
1. **Test de la connexion avec un hosts "Windows"**
Exemple:<br/>
``
ansible -i winhosts win -m win_ping
``<br/>
2. **Récupérer des "Facts"**<br/>
Avec le module "win_disk_facts" , récupérer les paramètres des disques de la VM Windows<br/>
exemple:<br/>
``
ansible-playbook -i winhosts info-disk.yml -v
``<br/>

3. **Executer les playbooks**<br/>
Pour initialiser, partitionner et formater :<br/>
``
ansible-playbook -i winhosts disk.yml -v
``<br/>
Pour ajouter le role ADDS et le paramétrer: <br/>
``
ansible-playbook -i winhosts ad.yml -v
``<br/>

4. **Ajouter un rôle "restart" dans le Playbook ad.yml"**<br/>
Création du rôle:<br/>
``
mkdir -p roles/restart/tasks
``<br/>
``
touch roles/restart/tasks/main.yml
``<br/>
Création du rôle restart:<br/>
https://docs.ansible.com/ansible/latest/modules/win_reboot_module.html<br>
Une fois le rôle "restart" et le "playbook ad.yml" modifié :<br/>
``
ansible-playbook -i winhosts ad.yml -v
``<br/>

