# TP 3 - Utilisateurs, groupes et permissions

## Exercice 1. Gestion des utilisateurs et des groupes
1. La commande pour créer le groupe dev est `sudo groupadd dev` et pour le groupe infra est `sudo groupadd infra`.
2. La commande pour créer un utilisateur demander la création de son dossier personnel et lui assigner le shell bash est `useradd --create-home --shell /bin/bash alice`.
3. La commande pour ajouter un utilisteur dans un groupe est `sudo usermod -a -G dev alice`.
4. Pour avoir tous les utilisateurs d'un groupe `infra` on peut faire `grep "infra" /etc/group | cut -d':' -f4` ou `getent group infra`
5. La commande qui permet de changer le groupe propriétaire d'un fichier est `sudo chgrp dev /home/alice`.
6. La commande pour changer le groupe primaire d'un utilisateur est `sudo usermod alice -g dev`.
7. La commande pour créer les dossiers `dev` et `infra` sont `sudo mkdir /home/dev` et `sudo mkdir /home/infra`. Pour changer les droits il suffit de faire `sudo chmod 660/home/dev`.
8. Pour que seul le propriétaire du fichier puisse le modifier il faut activer le sticky bit avec `sudo chmod 1660/home/dev`.
9. On ne peut pas ouvrir de session en tant que `alice` car l'utilisateur n'a pas de mot de passe donc le compte est désactivé.
10. La commande pour changer le mot de passe d'un utilisateur est `sudo passwd alice` puis pour se connecter a son shell il suffit de faire `su alice`.
11. Pour obtenir l’uid et le gid de alice il suffit de faire `id alice`.
12. Pour retrouver l’utilisateur dont l’uid est 1003 il suffit de faire `id 1003`.
13. L’id du groupe `dev` est `grep dev: etc/group` qui renvoie 1002 
14. Le groupe qui a pour gid 1002 est `grep :1002: /etc/group` qui renvoie `dev`.
15. Retirez l’utilisateur charlie du groupe infra. `sudo passwd --delete charlie infra` Que se passe-t-il ? L'utilisateur `charlie` ne pourra plus accéder au dossier infra.
16. Modifiez le compte de dave de sorte que : 
	* il expire au 1 er juin 2021 `sudo usermod -e 2021-06-01 dave`
	* il faut changer de mot de passe avant 90 jours `sudo chage -M 90 dave`
	* il faut attendre 5 jours pour modifier un mot de passe  `chage -m 5 dave`
	* l’utilisateur est averti 14 jours avant l’expiration de son mot de passe `sudo chage -W 14 dave`
	* le compte sera bloqué 30 jours après expiration du mot de passe `sudo chage -I 30 dave`
17. L’interpréteur de commandes (Shell) de l’utilisateur root est `/bin/bash`
18. Le compte `nobody` est celui dont aucun fichier n'appartient, qui n'est dans aucun groupe qui a des privilèges et dont les seules possibilités sont celles que tous les autres ont.
19. Par défaut, la commande sudo conserve en mémoire le mot de passe 15 minutes La commande qui permet de forcer sudo à oublier votre mot de passe est ``

## Exercice 2. Gestion des permissions
1. Les droits sur `test` sont `drwxrwxr-x` et `fichier` sont `-rw-rw-r--`.
2. L'utilisateur `root` est au dessus des droits car ici plus personne n'a de droit sur le fichier mais l'utilisateur root peux quand même y accéder.
3. Il est impossible d'écrire dans le fichier via une commande.
4. L'exécution du fichier ne fonctionne pas car la permission x n'est pas accordé sur l'utilisateur alors que le root lui a toutes les permissions sur tous les fichiers et dossiers du serveur.
5. Il est impossible de lister ou d'afficher quoi que se soit mais nous nous trouvons toujours dans le dossier.
6. Le droit d'écriture empèche juste d'écrire dans le fichier mais on peut toujours le lire et l'exécuter de plus le fichier peux être supprimer si le dossier a les droits d'écriture. Il est tout de même demandé si nous sommes sûr de vouloir supprimer le fichier nouveau en écriture seulement.
7. Le droit d'exécution ne permet pas de créer ou de modifier des fichiers dans le dossier ni de s'y déplacer.
8. Il est toujours impossible de faire quoi que ce soit cependant nous pouvont quand même revenir dans le dossier parent.
9. 
