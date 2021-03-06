# Introduction

## Qu'est-ce que atoum ?

atoum est un framework de test unitaire, tout comme PHPUnit ou SimpleTest, mais:

* il est moderne et utilise les innovations des dernières versions de PHP ;
* il est simple et facile à maitriser ;
* il est intuitif, sa syntaxe se veut la plus proche du language naturel anglais.


## Téléchargement et installation

Pour le moment, atoum n'a pas de version finale. Il est néanmoins d'ores et déjà stable et
utilisable.
Si vous souhaitez utiliser atoum, il vous suffit de télécharger la dernière version.
Malgré les évolutions constantes d'atoum, la rétro-compatibilité est une des priorités des développeurs.

Vous pouvez installer atoum de plusieurs manières:

* [en téléchargeant l'archive PHAR](#archive-phar) ;
* [en utilisant composer](#composer) ;
* [en utilisant un script d'installation](#script-dinstallation) ;
* [en clonant le dépôt github](#github) ;
* [en utilisant un plugin symfony 1](#plugin-symfony-1) ;
* [en utilisant un bundle symfony 2](#bundle-symfony-2).
* [en utilisant un composant zend framework 2](#composant-zend-framework-2).


### Archive PHAR

Une archive PHAR est créée automatiquement à chaque modification d'atoum.

PHAR (**PH**P **Ar**chive) est un format d'archive d'application PHP, disponible depuis PHP 5.3.

#### Installation

Vous pouvez télécharger la dernière version stable d'atoum directement depuis le site officiel:
[http://downloads.atoum.org/nightly/mageekguy.atoum.phar](http://downloads.atoum.org/nightly/mageekguy.atoum.phar)

#### Mise à jour

La mise à jour de l'archive est très simple. Il vous suffit de lancer la commande suivante:

    [shell]
    php -d phar.readonly=0 mageekguy.atoum.phar --update

**Note**: la mise à jour de d'atoum nécessite la modification de l'archive PHAR. Or par défaut, la
configuration de php ne l'autorise pas. Voilà pourquoi il faut utiler la directive
"-d phar.readonly=0".

Si une version plus récente existe, elle sera alors téléchargée automatiquement et installée au sein
de l'archive:

    [shell]
    php -d phar.readonly=0 mageekguy.atoum.phar --update
    Checking if a new version is available... Done !
    Update to version 'nightly-1568-201210311708'... Done !
    Enable version 'nightly-1568-201210311708'... Done !
    Atoum was updated to version 'nightly-1568-201210311708' successfully !

S'il n'y a pas de version plus récente disponible, atoum s'arrêtera immédiatement:

    [shell]
    php -d phar.readonly=0 mageekguy.atoum.phar --update
    Checking if a new version is available... Done !
    There is no new version available !

atoum ne demande aucune confirmation de la part de l'utilisateur pour réaliser la mise à jour
car il est très facile de revenir à une version précédente.

#### Lister les versions contenues dans l'archive

Pour afficher les versions contenues dans l'archive au fur et à mesure des mises à jours,
il faut faire appel à l'argument --list-available-versions, ou -lav en version abrégée:

    [shell]
    php mageekguy.atoum.phar -lav
    nightly-941-201201011548
    * nightly-1568-201210311708

La liste des versions présentes dans l'archive est alors affichée, la version actuellement active
étant précédée de "*".

#### Changer la version courante

Pour activer une autre version, il suffit d'utiliser l'argument --enable-version, ou -ev en version
abrégé, suivi du nom de la version à utiliser:

    [shell]
    php -d phar.readonly=0 mageekguy.atoum.phar -ev DEVELOPMENT

**Note**: la modification de la version courante nécessite la modification de l'archive PHAR. Or par 
défaut, la configuration de php ne l'autorise pas. Voilà pourquoi il faut utiler la directive
"-d phar.readonly=0".

#### Suppression d'anciennes versions

Au cours du temps, l'archive peut contenir plusieurs versions d'atoum qui ne sont plus utilisées.

Pour les supprimer, il suffit d'utiliser l'argument --delete-version, ou -dv dans sa version
abrégée, suivi du nom de la version à supprimer:

    [shell]
    php -d phar.readonly=0 mageekguy.atoum.phar -dv nightly-941-201201011548

La version est alors supprimée.

**Note**: il n'est pas possible de supprimer la version active.

**Note**: la suppression d'une version nécessite la modification de l'archive PHAR. Or par défaut,
la configuration de php ne l'autorise pas. Voilà pourquoi il faut utiler la directive
"-d phar.readonly=0".


### Composer

[Composer](http://getcomposer.org) est un outil de gestion de dépendance en PHP.

Commencer par installer composer

    [shell]
    curl -s https://getcomposer.org/installer | php

Créez, ensuite, un fichier composer.json contenant le JSON suivant: 

    [json]
    {
        "require": {
            "atoum/atoum": "dev-master"
        }
    }

Enfin, exécutez la commande suivante:

    [shell]
    php composer.phar install

### Script d'installation

Vous pouvez installer atoum grâce à un [script](https://github.com/atoum/atoum-installer) dédié:

    [shell]
    curl https://raw.github.com/atoum/atoum-installer/master/installer | php -- --phar
    php mageekguy.atoum.phar -v
    atoum version nightly-xxxx-yyyymmddhhmm by Frédéric Hardy (phar:///path/to/mageekguy.atoum.phar)

Vous pourrez facilement installer atoum localement (dans un projet, voir exemple précédent) ou globalement sur le système:

    [shell]
    curl https://raw.github.com/atoum/atoum-installer/master/installer | sudo php -- --phar --global
    which atoum
    /usr/local/bin/atoum

Des options sont disponibles pour personnaliser l'installation d'atoum : reportez-vous à
[la documentation (en)](https://github.com/atoum/atoum-installer/blob/master/README.md) de l'installer
pour obtenir plus de détails.

### Github

Si vous souhaitez utiliser atoum directement depuis ses sources, vous pouvez cloner ou forker le
dépôt github:
[git://github.com/atoum/atoum.git](git://github.com/atoum/atoum.git)


### Plugin symfony 1

Si vous souhaitez utiliser atoum au sein d'un projet symfony 1, un plugin existe et est disponible à
l'adresse suivante:
[https://github.com/agallou/sfAtoumPlugin](https://github.com/agallou/sfAtoumPlugin).

Toutes les instructions pour l'installation et l'utilisation d'atoum sont expliquées sur cette page.


### Bundle symfony 2

Si vous souhaitez utiliser atoum au sein d'un projet symfony 2, un bundle existe et est disponible à
l'adresse suivante:
[https://github.com/FlorianLB/JediAtoumBundle](https://github.com/FlorianLB/JediAtoumBundle).

Toutes les instructions pour l'installation et l'utilisation d'atoum sont expliquées sur cette page.


### Composant zend framework 2

Si vous souhaitez utiliser atoum au sein d'un projet zend framework 2, un composant existe et est
disponible à l'adresse suivante:
[https://github.com/blanchonvincent/zend-framework-test-atoum](https://github.com/blanchonvincent/zend-framework-test-atoum).

Toutes les instructions pour l'installation et l'utilisation d'atoum sont expliquées sur cette page.


## La philosophie d'atoum

### Exemple simple

Vous devez écrire une classe de test pour chaque classe à tester.

Imaginez que vous vouliez tester la traditionnelle classe HelloWorld, alors vous devez créer la
classe de test test\units\HelloWorld.

**NOTE**: atoum utilise les espaces de noms. Par exemple, pour tester la classe
\Vendor\Project\HelloWorld, vous devez créer la classe \Vendor\Project\tests\units\HelloWorld.

Voici le code de la classe HelloWorld que nous allons tester.

    [php]
    <?php
    # src/Vendor/Project/HelloWorld.php

    namespace Vendor\Project;

    class HelloWorld
    {
        public function getHiAtoum ()
        {
            return 'Hi atoum !';
        }
    }

Maintenant, voici le code de la classe de test que nous pourrions écrire.

    [php]
    <?php
    # src/Vendor/Project/tests/units/HelloWorld.php

    // La classe de test à son propre namespace:
    // Le namespace de la classe à tester + "tests\units"
    namespace Vendor\Project\tests\units;

    // Vous devez inclure la classe à tester
    require_once __DIR__ . '/../../HelloWorld.php';

    use \atoum;

    /*
     * Classe de test pour \HelloWorld

     * Remarquez qu'elle porte le même nom que la classe à tester
     * et qu'elle étend atoum\test
     */
    class HelloWorld extends atoum\test
    {
        /*
         * Cette méthode est dédiée à la méthode getHiAtoum()
         */
        public function testGetHiAtoum ()
        {
            // création d'une nouvelle instance de la classe à tester
            $helloToTest = new \Vendor\Project\HelloWorld();

            $this
                // nous testons que la méthode getHiAtoum retourne bien
                // une chaîne de caractère...
                ->string($helloToTest->getHiAtoum())
                    // ... et que la chaîne est bien celle attendu,
                    // c'est à dire 'Hi atoum !'
                    ->isEqualTo('Hi atoum !')
            ;
        }
    }

Maintenant, lançons nos tests:

    [bash]
    php vendor/mageekguy.atoum.phar -f src/Vendor/Project/tests/units/HelloWorld.php

Vous devriez voir quelque chose comme ça:

    [bash]
    > PHP path: /usr/bin/php
    > PHP version:
    => PHP 5.4.7 (cli) (built: Sep 13 2012 04:24:47)
    => Copyright (c) 1997-2012 The PHP Group
    => Zend Engine v2.4.0, Copyright (c) 1998-2012 Zend Technologies
    =>     with Xdebug v2.2.1, Copyright (c) 2002-2012, by Derick Rethans
    > Vendor\Project\tests\units\HelloWorld...
    [S___________________________________________________________][1/1]
    => Test duration: 0.02 second.
    => Memory usage: 0.00 Mb.
    > Total test duration: 0.02 second.
    > Total test memory usage: 0.00 Mb.
    > Code coverage value: 100.00%
    > Running duration: 0.34 second.
    Success (1 test, 1/1 method, 2 assertions, 0 error, 0 exception) !


Nous venons de tester que la méthode getHiAtoum:

* retourne bien une chaîne de caractère ;
* et que cette chaîne est bien celle attendu, c'est à dire 'Hi atoum !'.

Les tests sont passés, tout est au vert. Voilà, votre code est solide comme un roc grâce à atoum !


### Principes de base

Avec atoum, quand vous voulez tester quelque chose:

* spécifiez sur quoi vous voulez travailler (une variable, un objet, un tableau, une chaîne de
caractères, un nombre entier, etc...);
* indiquez dans quel état il doit être (égal à, null, contenant quelque chose, etc...).


## Intégration d'atoum dans votre IDE

## Sublime Text 2

Un [plug-in pour SublimeText 2](https://github.com/toin0u/Sublime-atoum) permet l'exécution des
tests unitaires par atoum et la visualisation du résultat sans quitter l'éditeur.

Les informations nécessaires à son installation et à sa configuration sont disponibles
[via le blog de son auteur](http://sbin.dk/2012/05/19/atoum-sublime-text-2-plugin/).

## VIM

atoum est livré avec un plug-in facilitant son utilisation dans l'éditeur VIM.

Il permet d'exécuter les tests sans quitter VIM et d'obtenir le rapport correspondant dans une
fenêtre de l'éditeur.

Il est alors possible de naviguer parmi les éventuelles erreurs,
voir de se rendre à la ligne correspondant à une assertion ne passant pas à l'aide d'une simple
combinaison de touches.

### Installation du plug-in atoum pour VIM

Si vous n'utilisez pas atoum sous la forme d'une archive PHAR, vous trouverez le fichier
correspondant au plug-in, nommé atoum.vba, dans le répertoire ressources/vim.

Dans le cas contraire, il faut demander à l'archive PHAR d'*atoum* d'extraire le fichier à l'aide de
la commande suivante:

    [shell]
    php mageekguy.atoum.phar --extractRessourcesTo path/to/a/directory

Une fois l'extraction réalisée, le fichier atoum.vba correspondant au plug-in pour VIM sera dans le
répertoire path/to/a/directory/ressources/vim.

Une fois en possession du fichier atoum.vba, il faut l'éditer à l'aide de VIM:

    [shell]
    vim path/to/atoum.vba

Il n'y a plus ensuite qu'à demander à VIM l'installation du plug-in à l'aide de la commande:

    [vim]
    :source %

### Utilisation du plug-in atoum pour VIM

Pour utiliser le plug-in, atoum doit évidemment être installé
et vous devez être en train d'éditer un fichier contenant une classe de tests unitaires basée sur
atoum.

Une fois dans cette configuration, la commande suivante lancera l'exécution des tests:

    [vim]
    :Atoum

Les tests se lancent alors, et une fois qu'ils sont terminés, un rapport basé sur le fichier de
configuration pour atoum qui se trouve dans le répertoire ftplugin/php/atoum.vim de votre répertoire
.vim est généré dans une nouvelle fenêtre.

Évidemment, vous êtes libre de lier cette commande à la combinaison de touche de votre choix,
en ajoutant par exemple la ligne suivante dans votre fichier .vimrc:

    [vim]
    nnoremap *.php :Atoum

L'utilisation de la touche F12 de votre clavier en mode normal appellera alors la commande :Atoum.

### Gestion des fichiers de configuration de atoum

Vous pouvez indiquer un autre fichier de configuration pour atoum en ajoutant la ligne suivante à
votre fichier .vimrc:

    [vim]
    call atoum#defineConfiguration('/path/to/project/directory', '/path/to/atoum/configuration/file', '.php')

La fonction atoum#defineConfiguration permet en effet de définir le fichier de configuration à
utiliser en fonction du répertoire ou se trouve le fichier de tests unitaires.

Elle accepte pour cela trois arguments:
* un chemin d'accès vers le répertoire contenant les tests unitaires ;
* un chemin d'accès vers le fichier de configuration de atoum devant être utilisé ;
* l'extension des fichiers de tests unitaires concernés.

Pour plus de détails sur l'utilisation du plug-in, une aide est disponible dans VIM via la commande
suivante:

    [vim]
    :help atoum
