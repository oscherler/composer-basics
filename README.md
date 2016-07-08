# Composer pour PHP : La Base de la Base

**Marie ʕʘᴥʘʔ Julien @mariejulien**  
À chaque fois que j'essaye de me renseigner sur une techno de dev (genre composer) j'ai cette sale sensation http://html9responsiveboilerstrapjs.com/ 

**Ölbaum @oscherler**  
@mariejulien Composer ca sert à installer les dépendances de ton projet PHP. Au plus simple tu trouves le nom de la dép dans le Read Me…

e.g. symfony/var-dumper, et tu tapes php composer.phar require symfony/var-dumper. Il va créer un fichier composer.json.

Ça liste tes déps. Ensuite il télécharge la lib en question et la met dans vendor, et crée un autoloader, qui te permet…

d'éviter de faire des require partout de tous les fichiers de la lib. A la place tu require __DIR__ . '/vendor/autoload.php'

Et quand tu utilises une classe, elle est trouvée automatiquement grâce à son namespace. Pour tester:
dump('hello');

Le fichier composer.lock liste les versions exactes installées des libs demandées et de toutes leurs dépendances.

Comme ça dans git tu commites les deux fichiers composer, mais pas vendor. Quand tu déploies, `composer install` remet tout.

Là, je crois que c'est la base de la base. Des questions?

**Marie ʕʘᴥʘʔ Julien @mariejulien**  
@oscherler Oui : tu peux reprendre à partir de "Composer ça sert à installer les dépendances" ? :D

**Ölbaum @oscherler**  
@mariejulien Le code dont tu as besoin mais que tu ne veux pas récrire toi-même. E.g. pour valider les numéros de téléphone internationaux.

 `composer require giggsey/libphonenumber-for-php`, `require(__DIR__ . 'vendor/autoload.php');` et puis les classes sont dispo.
 
