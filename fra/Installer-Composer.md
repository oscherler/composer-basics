# Installer Composer

Même la page de téléchargement de Composer a de quoi intimider. On nous assène directement des commandes cabalistiques :

	php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
	php -r "if (hash_file('SHA384', 'composer-setup.php') === 'e115a8dc7871f15d853148a7fbac7da27d6c0030b848d9b3dc09e2a0388afed865e6a3d6b3c0fad45c48e2b5fc1196ae') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
	php composer-setup.php
	php -r "unlink('composer-setup.php');"

À la place, pour commencer, nous allons nous borner à télécharger l’archive PHAR de Composer dans notre dossier de travail, et l’exécuter depuis là. Une archive PHAR, c’est une façon d’empaqueter tout le code d’un programme PHP dans un seul fichier que l’on peut exécuter directement. C’est directement inspiré des JAR de Java.

Celle de Composer se trouve sur la [page de téléchargement][download], le lien *Latest Snapshot* sous la rubrique *Manual Download*, ou à l’adresse suivante : <https://getcomposer.org/composer.phar>.

[download]: https://getcomposer.org/download/

Une fois téléchargée, on peut tester directement en tapant\* :

	shell$ php composer.phar --version
	Composer version 1.2-dev (5979db2e754bbce1190767be4b9c5f1da8df418a) 2016-07-07 09:16:21

Au moment d’écrire ces lignes, nous avons la version `1.2-dev` du 7 juillet 2016.



\* Les lignes commençant par `shell$` indiquent l’‘invite de commande’ (*shell prompt* en anglais) dans le terminal, il faut taper ce qui est écrit après le `$`, puis la touche *entrée*. Les autres lignes montrent ce que les commandes exécutées affichent.
