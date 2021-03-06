# Technologies du site

## Intégration

L'intégration se fait via le moteur de templates erb de rails. Côté client j'ai utilisé toute une liste d'outils pour améliorer la qualité du site et augmenter ma productivité.

### Outils utilisés

-	Modernizer

	Principale utilité est de tester si l'utilisateur à JavaScript activé. Pour pouvoir rendre le site dégradable.


-	jQuery

	Cette bibliothèque est chargée pour accélérer le développement du code JavaScript.
	
-	coffeeScript

	Pré-processeur javascript. Ce language rend l'écriture du javascript plus courte et rapide.

	
-	scss

	Pré-processeur CSS, qui rend la création des feuilles de styles vraiment puissant. Les fonctionnalités de SCSS utilisées sont la créations de variables globales, ajout des média-queries dans les éléments, utilisation de mixines pour des actions qui se répètent,… 

-	gmap

	Bibliothèque principale pour tous ce qui apparait sur les cartes: Le la création des tracés à l'affichage de ceux-ci.

-	Eloys

	C'est une bibliothèque qui facilite la manipulation des polyline avec google map. En effet, un grand nombre de fonctions (essentiellement de calcul) sont ajoutées. Par exemple des fonction de calcule de distance le long d'une polyline.

## Côté serveur

Détails des technologies utilisées côté serveur.

### Rails

J'ai décidé de développer ce projet avec Ruby on Rails pour plusieurs raisons:

-	Premièrement pour faire une nouvelle expérience. On a surtout travaillé avec PHP en cours, je voulais voir un autre langage par curiosité.
-	Ensuite ce framework est très utilisé dans le domaine du web, donc c'est un plus dans mon profil personnel.


#### Retour d'expérience

Ce framework est vraiment simple à prendre en main pour une personne qui a déjà une expérience avec un autre framework. Sur le site consacré à Ruby on Rails, il y a une partie concernant la documentation qui est vraiment bien détailée pour les bases. Ensuite, leur API est claire et documentée.

Mon expérience avec Laravel m'a beaucoup aidé car il est inspiré en grande partie de Rails. J'ai donc vite été en confiance avec l'organisation des fichiers et la logique générale. Le framework à aussi accéléré mon temps de développement. En effet, beaucoup de fonctionnalités sont déjà misent en place; comme travailler avec des pré-processeurs. De base scss et coffeeScript sont installer et le développeur n'a pas besoin de perdre du temps à configurer sont environement de travaille pour compiler ses assets.

Avec rails j'ai appris à ne pas me compliquer la tâche. Souvent je développais des parties du site et quelques semaines après en relisant le code, je supprimais la moitier pour donner un résultat identique. Plus je comprennais le framework, plus mon code devenais simple et efficace.

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

	Geocoder est un système de géocodage. Le principe est de lui donner des coordonées et il renvoit des données comme la ville, le pays,… Il permet aussi de faire des queries sur des modèles qui sont géocodé. C'est à dire que qu'on peu lui demander de lister les résultat proche de certaines coordonées et il va les lister en fonction de leur distance par rapport à cette position. Je l'utilise pour lister les tracés en fonction de la position de l'utilisateur.


-	dotenv-rails

	Gérer les variables d'environement. Le but est de protéger les données sensibles (mot de passes, clés secretes,… ) et de les retirer du contrôle de version (git).


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


### Base de donnée

Voici le schémas de la base de donnée en simplifié. C'est-à-dire que je ne montre pas les données stockées dans les tables mais surtout les relations entr elles.

Le plus complexe dans la base de donnée à été de permettre aux utilisateurs de créer leur tracé. J'ai essayé plusieurs approches.

Le premier moyen que j'avais mit au point était de proposer à l'utilisateur d'uploader un fichier de type tcx, gpx ou kml et je m'occupais de le parser pour l'afficher sur une map.

Ensuite j'ai décider de proposer à l'utilisateur de créer son tracé sur une map en directe, c'est à ce moment la que les problèmes on commencés. J'avais réussi à lui faire faire un tracé sur une map envoyer les données et avec celles ci je voulais générer un fichier kml pour le stocker dans un dossier «uploads» . La seule information dans la base de donné n'étant que le nom du fichier (d'ailleurs la première méthode fait pareil).

J'avais presque réussi à générer le fichier kml puis je me suis rendu compte que ma technique pour stocker l'information n'étais pas très flexible. Rester attacher à des fichier était un problème. En faisant des recherches sur internet j'ai trouvé qu'il y a deux techniques pour stocker des polylines (le tracé). 

J'ai d'abord choisi la première qui consistait à créer une table «tracks», une «tracksegments» et une «points». La «tracks» stocke les informations générales du tracé, «tracksegments« est une table pivot entre «tracks» et «points» et «points» stock tous les points (latitude, longitude) d'un tracé.

Cette solution est la plus flexible. Donc tout était fonctionnel: stocker un tracé dans la base de donnée manuellement à partir d'une map. Le seul problème (oui il y en a toujours) c'est la quantité énorme de ligne que cela prend dans la base de donnée. Pour 3-4 tracés j'en étais déjà à plusieurs millier de lignes dans la table «points»…

De plus je ne prévois pas d'exécuter des queries sur les cordonnées dans la table points (ce qui était le seul but de cette technique). J'ai donc opté pour la solution numéro deux.

Elle consiste à sérialiser une polyline en une chaine de caractère et simplement la stocker dans un champ texte. c'est plus simple et ça ne prend qu'une seule ligne par tracé. J'ai donc supprimé les tables «points» et «tracksegments» et je stocke le tracé dans la table «tracks».
