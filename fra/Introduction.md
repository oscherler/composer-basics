# Composer pour PHP : La Base de la Base

Une remarque pertinente de [@mariejulien][] sur Twitter :

> **Marie ʕʘᴥʘʔ Julien** @mariejulien  
> À chaque fois que j’essaye de me renseigner sur une techno de dev (genre composer) j’ai cette sale sensation http://html9responsiveboilerstrapjs.com/ [#][original-tweet]

m’a inspirée et cela m’a donné l’idée d’expliquer Composer en partant de la base de la base.

[@mariejulien]: https://twitter.com/mariejulien/
[original-tweet]: https://twitter.com/mariejulien/status/751109093566316544

Mon premier [brouillon en 10 tweets][tweets] (tapés sur mon téléphone en prenant mon premier café du matin), a donné ceci (corrigé, formaté, et sans les abbreviations) :

[tweets]: https://storify.com/oscherler/composer-de-base

Composer, ça sert à installer les dépendances de ton projet PHP. Au plus simple tu trouves le nom de la dépendance dans le Read Me, e.g. `symfony/var-dumper`, et tu tapes :

	shell$ php composer.phar require symfony/var-dumper
	
Il va créer un fichier `composer.json` qui liste tes dépendances.

Ensuite il télécharge la bibliothèque en question dans le dossier `vendor`, et crée un ‘autoloader,’ qui te permet d’éviter de faire des `require` partout de tous les fichiers de la bibliothèque. À la place, tu fais :

	require(__DIR__ . '/vendor/autoload.php');
	
et quand tu utilises une classe, elle est trouvée automatiquement grâce à son namespace. Pour tester (ici c’est une fonction, mais ça marche aussi) :

	<?php
	
	require(__DIR__ . '/vendor/autoload.php');
	
	dump('hello');

Le fichier `composer.lock` liste les versions exactes installées des bibliothèques demandées et de toutes leurs dépendances. Comme ça, dans git, tu commites les deux fichiers `composer.json` et `composer.lock`, mais pas le dossier `vendor`. Quand tu déploies, `composer install` télécharge tout ce qu’il faut.

Là, je crois que c’est la base de la base. Des questions ?

> **Marie ʕʘᴥʘʔ Julien** @mariejulien  
> Oui : tu peux reprendre à partir de “Composer ça sert à installer les dépendances” ? :D

Les dépendances, c’est le code dont tu as besoin mais que tu ne veux pas récrire toi-même. E.g. pour valider les numéros de téléphone internationaux :

	shell$ composer require giggsey/libphonenumber-for-php

puis :

	<?php
	
	require(__DIR__ . 'vendor/autoload.php');
	
	# Les classes de la bibliothèque en question sont maintenant disponibles pour utilisation.

	$phoneUtil = \libphonenumber\PhoneNumberUtil::getInstance();

	# ...
