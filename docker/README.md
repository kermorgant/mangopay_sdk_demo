-*- mode: org; -*-

* docker en mode developpement
** installer docker

   méthode rapide pour ubuntu :
   https://docs.docker.com/engine/getstarted/linux_install_help/

** installer docker-compose

   https://docs.docker.com/compose/install/

* Premier lancement
  Avant de pouvoir executer le code, il faut installer les librairies définies
  dans le fichier composer.json car elles ne sont pas dans le repo git (ça remplit le dossier vendor)

  #+BEGIN_SRC sh
$ docker-compose run --rm php  composer install --no-interaction
  #+END_SRC

  Après cela, on peut démarrer le "service" défini dans le fichier
  docker-compose.yml ainsi :

  #+BEGIN_SRC sh
$ docker-compose up php
  #+END_SRC

  Si tout se passe bien, l'application est accessible en local sur votre
  navigateur à l'adresse http://127.0.0.1:8000

* Deployer

** first setup
   Pour mémoire, j'ai fait ça pour suivre la doc mais j'ai largement repris le
fichier généré (voir deploy.php.dist).

  #+BEGIN_SRC sh
$ docker-compose run --rm php  dep init
$ docker-compose run --rm php  chmod 777 /var/www/deploy.php
  #+END_SRC

** Lancement du déploiement
  #+BEGIN_SRC sh
$ docker-compose run --rm php  dep deploy beta
  #+END_SRC
