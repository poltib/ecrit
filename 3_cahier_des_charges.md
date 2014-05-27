# Cahier des charges

Dans le monde de la course à pied, le plus intéressant après les entrainements c'est de participer à une course. Pour pouvoir se mesurer aux autres ou simplement vivre une expérience avec d'autres coureurs. Mais avant de participer à une course il faut en choisir et ça ce n'est pas toujours facile. Les publicités sont rares et les informations y figurant ne sont pas toujours ce que le coureur recherche. Souvent les deux informations les plus importantes sont la date et un détail du tracé. Malheureusement la deuxième est difficile à reproduire sur papier et quand bien même il est imprimé il serait bon de pouvoir manipuler la carte, inspecter le tracé sous toute ses coutures.

1. Donner accès à des évènements de course à pied aux sportifs

	-	Donc le premier besoin du site est de proposer des évènements de course à pied (au sens large: marche, course, Golden race,…) ou l'information principale est le(s) tracé(s). Il faut donc une interface qui affiche ce(s) tracé(s) sur une carte à l'aide d'une librairie externe (par exemple: Google map, Open Street Map,…). Il faudra donc afficher le tracé de manière précise et visible. Pour ajouter d'autres informations, un plus serait de proposer l'élévation le long du tracé (détail des changements d'altitude).
	
	-	Le second objectif est de proposer à l'utilisateur une liste de ces évènements avec des options de tri et un outil de recherche facile à prendre en main et efficace. Cette liste devra comporter des informations cruciales sur les évènements pour permettre aux utilisateurs de ne pas aller sur des pages d'évènements qui ne les intéressent pas. Par exemple donner les distances des tracé, la date, le lieu,…

2. Permettre la création de ces évènements aux organisateurs
	
	-	Ajouter une interface de création d'évènements simple. Il ne faut pas submerger l'utilisateurs de champs à remplir et de l'obliger à tout réaliser d'un coup. Donc la création devra être séparée en plusieurs étapes simple. La première est d'encoder les information générales; nom, date, description,… Ensuite il faudra donner accès à une interface de création de tracés pour pouvoir en ajouter aux évènements.
	
	-	La création de tracé sur une carte devra être intuitive et accompagner l'utilisateur si c'est sa première utilisation. 
	
	-	Un plus serai de permettre aux utilisateurs d'ajouter un tracé à partir d'un fichier (de type .tcx, .gpx ou .kml par exemple).
	
	-	Une autre donnée importante pour les organisateurs est les participants aux évènements. Il faut donc donner la possibilité aux utilisateurs de participer aux évènements.
	
	-	Dans la même optique, pour augmenter la visibilité de leur publication il faut ajouter une option de partage. L'idée est d'ajouter des liens pour partager le contenu du site sur les réseaux sociaux, ou par mail.
	
	-	Également donner la possibilité de modifier et supprimer ces évènement.
	
2. Donner accès aux tracés

	-	Vu que les tracés sont la base des évènements donc du site. Il est normal de proposer aux utilisateurs une partie qui leurs est entièrement consacrée. Et par la même occasion proposer de nouvelles fonctionnalités.

	-	Rendre les tracer téléchargeables. Beaucoup de personnes pratiquant la randonnées ou la course à pied aiment planifier leurs activités. L'idée est donc de répondre à ce besoin eu leur donnant accès à l'éditeur de tracé indépendamment des évènements, et après création rendre le tracé exportable en plusieurs types de fichiers (.gpx, .kml, .tcx,…).