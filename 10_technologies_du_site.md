# Technologies du site

## Intégration

### Outils utilisés

-	Modernizer
-	jQuery
-	coffeeScript
-	scss
-	Turbolinks
-	gmap
-	Eloys

## Côté serveur

### Rails

J'ai décidé de développer ce projet avec Ruby on Rails pour plusieurs raisons:

-	Premièrement pour faire une nouvelle expérience. On a surtout travaillé avec PHP en cours, je voulais voir un autre langage par curiosité.
-	Ensuite ce framework est très utilisé dans le domaine du web, donc c'est un plus dans mon profil personnel.

#### Retour d'expérience

Ce framework est vraiment simple à prendre en main pour une personne qui a déjà une expérience avec un autre framework. Sur le site consacré à Ruby on Rails, il y a une partie concernant la documentation qui est vraiment bien détailée pour les bases. Ensuite, leur API est claire et documentée.

Mon expérience avec Laravel m'a beaucoup aidé car il est inspiré en grande partie de Rails. J'ai donc vite été en confiance avec l'organisation des fichiers et la logique générale. 

### Postgres


# Technologies du site

## Intégration

### Outils utilisés

-	Modernizer
-	jQuery
-	coffeeScript
-	scss
-	Turbolinks
-	gmap
-	Eloys

## Côté serveur

Détails des technologies utilisées côté serveur.

### Rails

J'ai décidé de développer ce projet avec Ruby on Rails pour plusieurs raisons:

-	Premièrement pour explorer. On a surtout travaillé avec PHP en cours, je voulais voir un autre langage par curiosité.
-	Ensuite ce framework est très utilisé dans le domaine du web, donc c'est un plus dans mon profil personnel.

#### Retour d'expérience

Ce framework est vraiment simple à prendre en main pour une personne qui à une expérience avec un autre framework. Sur leur site il y a une partie documentation qui est vraiment bien détailée pour les bases. Ensuite leur API est claire et documentée.

Mon expérience avec Laravel m'a beaucoup aidé car c'est inspiré en grande partie de Rails. J'ai donc vite été en confiance avec l'organisation des fichiers et la logique général. Ce framework à aussi accéléré mon temps de développement. En effet, beaucoup de fonctionnalités sont déjà misent en place; comme travailler avec des pré-processeurs. De base scss et coffeeScript sont installer et le développeur n'a pas besoin de perdre du temps à configurer sont environement de travaille pour compiler ses assets.

#### Ruby gems

Les gems sont à Ruby ce que sont les packages à PHP. Il existe un grand nombre de gems dans le monde de Ruby, toutes ressencées sur [rubyGem](https://rubygems.org/). Voici la liste des gems utilisées dans mon projet, leur avantages et pourquoi j'ai décidé de travailler avec.

-	turbolinks

	Cette technologie permet d'accélérer considérablement la navigation sur le site. En effet, cela utilise ajax pour recharger seulement le contenu de la page qui change. Le but est améliorer l'expérience utilisateurs avec de chargements de page plus rapides.
	
	-	jQuery-turbolinks
	
		Cette gem rend l'utilisation de jQuery avec turbolinks possible. Car à cause de turbolinks, les page ne sont plus rechargée durant la navigation sur le site, cela peu provoquer des bugs avec jQuery car les noeuds liés aux évènements n'existent plus. Cette gem lie les évènements déclanchés par turbolinks à jQuery.
-	devise

	Gem gérant toute la partie compte d'utilisateurs, connexion, sessions,... Ayant choisi de développer mon PFE en Ruby assez tardivement j'ai du faire des choix pour rattraper le temps perdu. Devise fait partie de ces choix. Le gain de temps que 
j'ai gagné grâce à cette gem est considérable. 

	-	omniauth
	
		Ceci est une extension de Devise. C'est pour permettre aux utilisateurs de se connecter via facebook à l'application.
		
-	carrierwave

	Carriewave se charge de l'upload des fichiers. 
	
	-	fog
	
		Gère les connexions vers des clouds. Je l'utilise pour connecter carriewave à Amazon s3.
		
	-	mini_magick
	
		Mini_magick est utilisé pour la manipulation d'image. Par exemple, les images des profils utilisateurs sont misent à l'échelle, et pour ne pas déformer les images il faut les recadrer. Mini_magick est une bibliothèque qui permet d'effectuer ces actions avec une grande simplicité.
		
-	nogokiri

	Nogokiri est un parser (html, xml). Un des objectif du site est de créer des tracés et de permettre aux utilisateurs de les exporter. Les fichiers exportés (.gpx) sont au format xml et Nogokiri est aussi un outil de création de fichiers.
	
-	autoprefixer-rails

	Préfixer automatiquement les règles CSS.
	
-	bourbon

	Bibliothèque SASS pour utiliser Neat.
	
	-	neat
	
		Neat est un système de grille SASS.
		
-	polyline

	Permet d'encoder des tableau de coordonées en polylines google. C'est polylines encodées permettent de prendre moins de place dans la base de donnée. Pour récupérer les coordonées il suffit de faire un appel à l'API googlemap.
	
-	geocoder

-	dotenv-rails

-	redcarpet

	Parser Markdown pour les forums.
	
-	will-paginate

	Gérer la pagination.


### Heroku

En début d'année je me suis acheté un hébergement chez OHV. Malheureusement ils ne permettent pas d'utiliser ruby sur leurs serveurs. J'ai donc dû checher une solution et un de mes objectif était de faire le moins de dépenses possible (j'avais envie de me fixer une limite de frais pour débelopper et mettre en ligne une première version).

Mon choix c'est donc naturellement tourné vers [Heroku](heroku.com).

Cet hébergeur permet de déployer rapidement des applications. Grâce à une configuration simple et beaucoup d'outils mit à notre disposition. L'avantage est que le code en ligne est sur un dépôt git, et chaque fois que l'on veut pousser des changement sur le site en ligne il suffit de faire un commit sur ce dépôt git. Heroku se charge du reste; comme la compillation des assets, mise à jour des gems,...

L'autre gros avantage est que le service est gratuit. C'est assez important car cela permet de tester de nouveaux projets en ligne rapidement et sans avoir de serveur. Il y a des restrictions dans la taille de la base de donné et certain plugins bien évidement.

Bien qu'Heroku m'a permit de gagner beaucoup de temps, il devait y avoir une contrepartie à cette gratuitée. Et cette contrepartie est que tous les fichiers uploadés par les utilisateurs sont supprimés après chaques commit. Je ne m'en étais pas rendu compte directement et j'ai vite du trouver une solution à ce problème. Effectivement, ne pas pouvoir faire évoluer le site sans supprimer les fichiers des utilisateurs ce n'est pas possible.

### Amazon s3

La solution (pour rester dans la gratuité), fut d'uploader les fichiers des utilisateurs sur un cloud. Mon choix s'est dirigé vers amazon web service qui propose un cloud avec 5giga d'espace gratuit. Pour la première mise en ligne de Sportfun c'est plus que suffisant, car dépasser les 5giga avec des images et des fichiers .gpx il faut beaucoup d'utilisateurs, ce qui me laisse le temps de prévoir (ou soit passer à la version payante).

Ce service est vraiment simple à utiliser et amène beaucoup d'avantage pour le développement d'application web. Par exemple si je veux changer d'hébergement il me suffit d'exporter la base de donnée, pousser mon code sur le nouveau serveur, importer la base de donnée et les fichiers seront toujours accessibles. Si j'ai un problème sur le serveur les fichiers des utilisateurs sont en sécurité.



