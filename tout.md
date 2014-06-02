# 1.Note d'intention

Détails de la conception du site [Sportfun](sportfun.herokuapp.com).

[Code source](https://github.com/poltib/pfeR)

En passant par la création du cahier des charges, définition du public cible, conception de l'interface, analyse de l'utilisabilité et de l'accessibilité pour finir par les détails techniques. Ce livre survolera toutes les étapes par lesquelles je suis passé pour développer cette application.

# 2.Motivation personnelle

Le projet de fin d'édute a été pour moi une façon de me mettre à l'épreuve. Concrètement, je me suis fixé une liste d'objectifs à réaliser (chaqun lié à une technologie différente). C'est en travaillant de la sorte que j'ai pu aquérir de nouvelles connaissances tout en développant mon projet de fin d'étude. Au final c'est cela qui m'a le plus motivé.

Je pratique également la course à pied. J'ai donc de la chance de me retrouver dans la peau de mes utilisateurs, comprendre leurs attentes, leur motivation mais également d'en cotoyer beaucoup. C'est quelque chose qui me pousse à donner le meilleur de moi-même.

### Objectifs

-	#### Développer une plateforme de partage

	Mon but premier, qui était en même temps ma plus grande motivation était de réaliser une application qui sert à être partagée. Comme permettre aux utilisateurs d'avoir accès à une bibliothèque de tracés d'entrainements et de pouvoir partager les leurs. Mon but était donc de créer un esprit de communauté autour du site, permettant aux utilisateurs l'utilisation en toute confiance, d'une manière agéable et aisée.
-	#### Manipuler des données géographiques
	
	J'ai toujours été fortement intéressé par tout ce qui concerne carte interactive sur l'internet. Mon sujet de projet se prêttais bien à l'utilisation de cette technologie alors j'en ai profité pour améliorer mes connaissances la-dessus. Ici, j'ai utilisé l'API de google map car nous l'avions vu en cours et aussi parce que je trouve leur site de référence très compréhensible. Mais au finale, l'idée principale est de pouvoir être indépandant de ce genre de librairie. Etant donné que le nombre de requêtes par jour sont limités, il est préférable de pouvoir changer de librairie facilement si l'application prend de l'ampleur. Pouvoir changer vers OpenStreetMap serait parfait par example.
	
-	#### Apprendre un nouveau language

	En cours nous avons eu une introduction au PHP (fin de deuxième année), et une introduction au framework Laravel également en PHP. Bien que je trouve ce framework exceptionel et que j'adore développer des applications avec, j'ai pensé que cela pouvais être utile de regarder ce qui se faisait ailleurs. J'ai donc développé mon application à l'aide du framework Ruby on Rails (qui utilise le language Ruby). Ce deuxième point m'a vraiment motivé dans mon développement; autant pour la syntaxe simplifiée du language, que pour la rapiditée avec laquelle on peut prendre en main le framework. Tout m'a séduit et j'ai vraiment pris plaisir à développer ce projet.
	
-	#### Bonne modélisation de base de donnée

	En plongeant dans Ruby on Rails, j'ai découvert que beaucoup de personnes utilisent postgresSql comme base de données relationnelle. J'ai aussi appris qu'il y a des extentions pour faciliter la manipulations de données géolocalisées, ce qui justement est super utile dans le cas de mon application. J'ai donc décidé d'utiliser cela pour la base de données. J'avais comme objectif de modéliser une base de données qui serait la plus extensible possible. En prévoyant également l'ajout possible de nouvelles fonctionalités.
	
-	#### Affichage de données complexes

	Pour afficher les données proposées aux utilisateurs j'ai décidé d'utiliser des graphiques. C'est parlant et quand ils sont bien mis en forme ils valent plus que n'importe quel texte. Parmis mes objectifs j'ai prévu également d'utiliser la superbe librairie d3 pour l'affichage des graphiques. Malheureusement, par manque de temps j'ai utilisé celle de google. Charts pour l'élèvation le long de tracés sur les cartes. Je ne comprends pas la rernière phrase


# 3.Cahier des charges

Dans le monde de la course à pied, le plus intéressant après les entrainements c’est de participer à une course. Pour pouvoir se mesurer aux autres ou simplement vivre une expérience avec d’autres coureurs. Mais avant de participer à une course, il faut en choisir une et ce n’est pas toujours facile. Les publicités sont rares et les informations y figurant ne sont pas toujours telles que le coureur recherche. Souvent, les deux informations les plus importantes sont la date et un détail du tracé. Malheureusement, la deuxième est difficile à reproduire sur papier et quand bien même il est imprimé, il serait bon de pouvoir manipuler la carte, inspecter le tracé sous toutes ses coutures.
## Pour les organisateurs
Ils n'y aurait pas de courses sans organisateurs. Donc le premier objectif du site est de séduire ces organisateur. Les mettre en confiance pour qu'ils viennent poster leur courses sur le site.
	Le site permettra aussi aux coureurs d'ajouter les courses eux même. L'idée est de véhiculer un esprit de partage; les coureur qui trouveront des courses intéressantes les partageront sur le site pour en faire profiter les autres utilisateurs.

### Permettre la création de ces évènements aux organisateurs
	
Ajouter une interface de création d'évènements simples. Il ne faut pas submerger l'utilisateur de champs à remplir et de l'obliger à tout réaliser d'un coup. La création devrait donc être séparée en plusieurs étapes simples. La première est d'encoder les informations générales; nom, date, description,… Ensuite, il faudra donner accès à une interface de création de tracés pour pouvoir en ajouter aux évènements. Également donner la possibilité de modifier et/ou supprimer ces évènement.
	
La création de tracé sur une carte devra être intuitive et accompagner l'utilisateur lors de sa première utilisation. Ce processus devrat être rapide, simple et efficace. L'utilisateur ne doit pas être découragé par l'utilisation de cet outil. Un plus serait de permettre aux utilisateurs d'ajouter un tracé à partir d'un fichier (de type .tcx, .gpx ou .kml par exemple).
	
Une autre donnée importante pour les organisateurs c'est la participation aux évènements. Il faut donc donner la possibilité aux utilisateurs de participer aux évènements. Ensuite lister ces participants.
	
Dans la même optique, pour augmenter la visibilité de leur publication, il faut ajouter une option de partage. L'idée est d'ajouter des liens pour partager le contenu du site sur les réseaux sociaux, ou par mail. Et finalement permetre aux utilisateur d'ajouter l'évènement à leurs favoris, comptabiliser ce nombre de favoris et ainsi départager les évènements par les utilisateurs.

## Pour les sportifs

### Donner accès à des évènements de course à pied aux sportifs

Le premier objectif du site pour les utilisateurs est de proposer des évènements de course à pied (au sens large: marche, course, Golden race,…) ou l'information principale est(sont) le(s) tracé(s). Il faut donc une interface qui affiche ce(s) tracé(s) sur une carte à l'aide d'une librairie externe (par exemple: Google map, Open Street Map,…). Il faudra donc afficher le tracé de manière précise et visible. Ensuite, ajouter d'autres informations, un plus serait de proposer l'élévation le long du tracé (détail des changements d'altitude).
	
Le second objectif est de proposer à l'utilisateur une liste de ces évènements avec des options de tri et un outil de recherche facile à prendre en main et efficace. Cette liste devra comporter des informations cruciales sur les évènements pour permettre aux utilisateurs un gain de temps dans leur recherche et ne pas les renvoyer sur des pages d'évènements qui ne les intéressent pas. Par exemple donner les distances des tracé, la date, le lieu,…
	
### Donner accès aux tracés

Vu que les tracés sont la base des évènements donc du site, il est normal de proposer aux utilisateurs une partie qui leurs est entièrement consacrée. Et, par la même occasion, proposer de nouvelles fonctionnalités.

Tous les tracés créés, que ce soit pour un évènement, ou un tracé tout court, seront listé dans une section «Tous les tracés». Cette section devra les afficher de manière interactive et en fonction de la position de l'utilisateur.

Sur la page de chaque tracé endre les tracer téléchargeables. Beaucoup de personnes pratiquant les randonnées où la course à pied aiment planifier leurs activités. L'idée est donc de répondre à ce besoin en leur donnant accès à l'éditeur de tracé indépendamment des évènements, et après le création rendre le tracé exportable en plusieurs types de fichiers (.gpx, .kml, .tcx,…).

### Donner accès à des groupes d'entrainements

La course à pied est un sport individuel, ce qui implique une grande force d'esprit. Malheureusement, ce n'est pas inné et cette force se forge aux cours de nombreuses heures d'entrainements. Le fait d'aller s'entrainer seul est souvent un gros problème pour les débutants. Il existe bien des clubs mais beaucoup de personnes pratiquent ce sport pour le plaisir. Il leurs faut donc un moyen de trouver des groupes d'entrainements près de chez eux.

Tout d'abord, afficher les groupes à proximité de l'utilisateur (sur une carte ou en liste). Pour proposer les groupes sucebtibles de l'intéresser le plus. La page d'un groupe devrait être capable de regrouper les informations les plus importantes aux yeux des utilisateurs. Comme la fréquences des activités, le nombre de membres et une description du genre de groupe.
	
Ensuite prévoir la création de groupe. Car pour que des gens trouvent des groupes, d'autres doivent les créer. La création de groupes devra être une étape simple et rapide pour les utilisateurs, car leur activité principale sera de le gérer.

Ces créateur devront donc avoir accès à une interface d'administrateur qui permettra d'effectuer plusieurs actions. Comme par exemple, accèpter les demandes d'adhésion, supprimer des utilisateurs du groupe, ajouter des activités au groupe,… 


### Créer un environement «communautaire»

Finalement, le site devra créer un esprit d'entraide, car c'est une valeur de base quand on est sportif. Le but est donc de permettre aux utilisateurs de pouvoir consulter la communauté, en postant des forums.
		
Il faut donc prévoir une partie «forum» pour permetre aux utilisateurs de communiquer entre eux. Pour accompagner les forums, et faciliter leurs utilisation, des catégories pourront être associées à ceux-ci. Les utilisateurs pourront répondre à ces forums en postant des réponses et ainsi donner vie au site.
	
Enfin, ajouter la création de forums sur les tracés et les évènements. De sorte, que les utilisateurs puissent donner leurs avis, discuter,… Il faut pouvoir lier les forums aux évènements et tracés, car le fait d'avoir des sujets de conversations sur ces éléments augmentera leur poids en informations, car l'avis d'autres personnes est très important pour les utilisateurs.

	
# 4.Public cible

La création du public cible est une étape importante. Après avoir définit les objectifs du site en tant que propriétaire, il est temps de définir les attentes des futurs utilisateurs. Pour pouvoir définir ces attentes, il faut d'abord donner vie à ces personnages, car plus ils auront l'air vrai, plus leurs exigeances seront claires et détaillées. Et en fonction de ces exigeances seront décidés les priorités de développement, et les directions de conception d'interfaces.

Pour commencer le site n'attirera pas que des utilisateurs intéressés dans toutes les fonctionnalités, car tous les utilisateurs sont différents. Pour «mimer» cette différence, j'ai créer différent niveaux de personnas (comme le conseille Amélie Boucher dans son livre «Ergonomie web»). Il y aura donc les personnas primaires: les utilisateurs de base du site. Les personnas secondaire: ceux qui utiliseront le site pour certaines fonctionnalités. Et enfin les personnas tertiaires: les utilisateurs qui viendront que pour une ou deux fonctionnalités.

## Primaires

### Séba
---

#### Description

C'est un travailleur normal et pendant son temps libre,  il pratique la course à pied. De ce fait, certains week-ends, il aime bien participer aux courses/joggings seul ou avec ses amis. Il s'entraine plusieurs fois par semaine dont plusieurs fois avec son groupe d'amis.

Il aime bien avoir un accès facile aux courses près de chez lui. Certains sites lui donnent déjà accès à beaucoup d'informations de ce genre (Go running, Chronorace).

Il aime aussi changer d'itinéraire d'entrainement. Pouvoir avoir accès à une bibliothèque de tracés serait un must.

Il aimerait aussi avoir un moyen pratique d'organiser ses entrainements avec ses amis. Devoir passer par facebook ou s'organiser par téléphone est souvent pénible. 

#### Antécédents

-	[Chronorace](http://www.chronorace.be/web2/default.aspx)
-	[Go running](http://www.gorunning.be/index_fr.php)

#### Ses attentes

Une interface simple et rapide pour effectuer ses tâches.

#### Attentes sur sportiveFun

##### Trouver des courses à proximité de chez lui

-	Avoir accès à un calendrier reprenant les courses à venir.
-	Pouvoir trier les courses en fonction de la date, code postal, distance ou pays.
-	Pouvoir avoir un aperçu rapide du tracé de la course et du dénivelé.
-	Pouvoir partager la course à ses amis.
-	Confirmer sa participation et inviter ses amis.

##### Organiser ses entrainements avec son groupe d'amis

-	Faire partie d'un groupe d'entrainement et en être le modérateur.
-	Créer un planning d'entrainement.
-	Sélectionner des tracés d'entrainements pour chaque entrainement.
-	Gérer les participants.

##### Trouver des nouveaux tracés d'entrainements

-	Avoir accès à une liste des tracés d'entrainements d'utilisateurs.
-	Pouvoir trier cette liste par distance, lieux et difficulté.
-	Ajouter ses propres tracés à la bibliothèque.
-	Ajouter des tracés à ses favoris.
-	Télécharger le tracé en .gpx.


### Julie
---

Julie est une organisatrice de courses et du jogging. Elle aime quand les participants sont satisfaits et reçoivent toutes les informations de manière claire et précise (Lieu de départ, distances, ravitaillements, facilitées autour de la course, résultats,..). Pour les résultats justement, elle fait appel à Chronorace qui est réputé pour fournir les résultats et les appareils de chronométrage. Ce qui lui manque,  c'est une plateforme ou elle pourrait proposer ses courses à des coureurs (un peu comme Go running), mais où la dimension sociale de la plateforme pousse les utilisateurs à partager les courses au plus grand nombre de personnes possibles.

Elle gère aussi un club de course à pied et elle recherche un outil pour pouvoir mieux le gérer. Par la même occasion si elle peut en faire de la pub à toute une communauté, c'est encore mieux.

#### Antécédents

-	[Go running](http://www.gorunning.be/index_fr.php)

#### Ses attentes

Pouvoir créer des courses facilement et les partager sur le plus de réseaux possibles.

#### Tâches sur sportiveFun

##### Ajouter des évènements

-	Avoir un rôle lui permettant d'ajouter des évènements.
-	Une interface de création intuitive qui rend cette création aisée.
-	La possibilité d'ajouter le tracer de la courses de plusieurs format (.tcx, .klm, .gpx) ou de le faire manuellement.
-	Inviter les utilisateurs à sa course et pouvoir en parler avec eux sur un forum dédié.
-	Poster les résultats après la course (interface automatique?).
-	Poster des photos de la course.
-	Poster les sponsors de la course.

##### Gérer son club

-	Plannifier les entrainements.
-	Gérer les membres.
-	Avoir un aperçu des participations des membres aux entrainements.
-	Pouvoir communiquer des annonces aux membres.



## Secondaires

### Jean
---

Jean est un jeune étudiant en éducation physique. En plus du sport pratiqué durant ses études, il s'entraine beaucoup en course à pied. Il adore découvrir de nouveaux chemins et les partager avec ses amis. 

#### Antécédents

-	[Go running](http://www.gorunning.be/index_fr.php)

#### Ses attentes

Pouvoir créer des courses facilement et les partager sur le plus de réseaux possibles.

#### Tâches sur sportiveFun

##### Ajouter des entrainements

-	Poster des tracés d'entrainements.
-	Partager ses tracés

### Charles
---

C'est un novice en course à pied. Il avait envie d'un nouveau hobby et il pensait souvent à se mettre à la course à pied. Il recherche une communauté qui pourrait l'aider dans ses choix (entrainements, équipements,…). Il est aussi à la recherche de personnes avec qui il pourrait courir. Car certains jours, trouver la motivation pour aller courir tout seul est difficile. Une autre source de motivation pour lui, est de partager ses résultats. Pour cela, il utilise des applications comme runtastic et strava pour observer sa progression, ses calories brulées, ...

#### Antécédents

-	[Runtastic](https://www.runtastic.com/fr)
-	[Strava](http://www.strava.com/)

#### Ses attentes

Il recherche une communauté qui l'aidera à débuter ce sport. Il recherche des conseils de qualité pour les entrainements, les équipements et pourquoi pas des joggings à participer. Il aimerait aussi trouver un groupe de personnes avec lequel il pourrait courir. Par contre, il n'attend pas d'un site d'analyse d'entrainements, il est déjà satisfait avec Strava.

#### Tâches sur sportiveFun

##### Parcourir les forums

-	Pour rechercher des conseils.
-	Poster des forums pour demander des conseils.

##### Rechercher un groupe d'entrainement

-	Trouver des personnes à proximité de chez lui pour s'entrainer en groupe.
-	Intégrer un groupe où la planification d'entrainement est déjà réalisée.
-	Interagir avec ce groupe dans la partie privée du groupe.

---

## Tâches principales du site selon les personas

### Trouver des courses/joggings/marches
-	Avoir accès à une liste filtrable selon certains critères (distance, lieu et date).
-	Pouvoir partager ces évènements et les ajouter aux favoris.
-	Permettre la création de courses (rôles).

### Trouver un groupe d'entrainement

-	Avoir une liste des personnes/groupes qui s'entrainent en course à pied à proximité de chez sois.
-	Intégrer ces groupe et avoir une interface de gestion des entrainements simple et efficace.
-	Permettre la création de groupe d'entrainement.

### Trouver des conseils

-	Une section forum avec des catégories et sous catégories.
-	Permettre au utilisateur de poser des questions ou poster des conseils.

### Trouver des tracés d'entrainements

-	Mettre à disposition une liste de tracés filtrable (distance, lieu, difficulté et les plus appréciés).
-	Permettre le partage de ces tracés.
-	Permettre de télécharger le tracé dans certains formats (.tcx, .gpx, .klm).

### Créer des tracés

-	Interface de création simple et rapide.
-	Télécharger les tracés (.gpx).

### Trouver un club

-	Permettre aux clubs d'augmenter leur visibilité grâce au site.
-	Leur fournir une interface pour gérer leurs membres et les entrainements.
-	Gérer la participation des membres aux entrainements.


# 5.Analyse de l'existant

Cette partie est consacrée à l'analyse des sites existants qui offre un service comparable à celui de Sport fun (ou en partie). C'est une partie très importante qui permet de voir ce qui a déjà été réalisé et de quelle manière.

Dans la plupart des projets, l'idée a déjà été trouvée, réalisée, améliorée, modifiée, le concept principal n'est pas de trouver l'idée du siècle (même si çela peut toujours être un plus), mais ce qui est important, c'est de quelle façon le produit sera proposé à l'utilisateur, concrètement, d'une manière à lui donner l'expérience la plus agréable et efficace mais également facile d'utilisation et plaisante.

C'est donc important d'analyser les sites du même type, qui ont déjà été réalisés. Voir s'ils ont réussi et si oui, pourquoi, retenir les points forts et les points faibles pour, finalement, en reprendre le meilleur et améliorer les faiblesses.

### [GoRunning](http://www.gorunning.be/index_fr.php)

GoRunning est un site sur la course à pied. Il propose plusieurs services:

-	Calendrier d'évènements
	
	Leur calendrier est intuitif et les informations pour chaque évènement sont très détaillées. Malheureusement, ils ne permettent pas de voir les tracés sur une carte. Et finalement; je trouve (c'est un avis personnel) que la mise en page est fort brute. Le formulaire d'encodage d'information est extrêment long.
	
	![Formulaire de création](img/5_1.png)
	
	Un point fort est la création d'une section pour les organisateurs. De sorte qu'ils entretiennent un lien avec les organisateurs, et ainsi sont certain des informations proposées sur les évènements.
	
-	Liste de magasins

	C'est une bonne idée à garder à l'esprit pour les prochaines fonctionnalités.


### [Chronnorace](http://www.chronorace.be/web2/default.aspx)

Chronorace est un fournisseur du matériel de chronométrage pour les courses. Ils proposent donc tous les résultats utilisant leur matériel sur leur site. C'est une mine d'informations pour tout coureurs voulant garder une trace de ses résultats, ou bien de retrouver ses résultats pour un évènement donné.

Leur site est fort basic car ils proposent beaucoup d'informations à la fois. Mais il à l'air de bien fonctionner auprès des coureurs vu que beaucoup de sites renvoient leurs utilisateurs ici pour les résultats d'évènements.

### [Mapometer](http://gb.mapometer.com)

Mapometer est un site de création de tracé. C'est surtout l'interface qu'ils ont dévelopé avec google map qui est intéressante. L'utilisateur a à sa  disposition une quantité d'outils imprésionante. Parfois ça devient même un peu trop compliqué, j'ai du tester plusieurs fois chaque outil pour être certain de leur utilitée; un accompagnement pour les nouveaux utilisateurs serait un plus.

![Formulaire de création](img/5_5.png)

Enfin en parcourant leur site je suis tombé sur une fonctionnalité très intéressante. J'ai créé un tracé sur la carte, puis j'ai changé de page sans le sauvegarder, et finalement en revenant sur la page de la carte le site propose de restaurer le tracé.
 

### [Strava](www.strava.com)

Strava est un site qui accompagne les sportifs prendant et après leurs entrainements. Ce site a vraiment su cibler son public et lui donner exactement ce dont il avait besoin. Cela va de la récupération des données de course (tracé, allure, dénivellé, fréquence cardiaque) à l'analyse de celle ci et l'interaction avec les autres utilisateurs. Et comme bonnus, ils organisent des challenges ou ils mettent les utilisateurs au défit et les gagants remportent des cadeaux.

J'ai passé beaucoup de temps sur ce site pour prendre de l'inspiration, observer leur interfaces et utiliser leur site pour m'entrainer. Leur interface de création de tracé est aussi très bien développée; les contrôles sont intuitifs et l'aide est bien présente pour guider les utilisateurs.

J'ai repris beaucoup d'idées de ce site; comme l'organisation globale de la page et des menu de navigation. 

Un des points fort de leur site est qu'il insite l'utilisateur à participer. Il y a des suggestions d'autres utilisateurs à suivre, de rechercher des clubs, proposer des challenges.

![Formulaire de création](img/5_2.png)

![Formulaire de création](img/5_3.png)

Ils proposent aussi une section «shop» où ils vendent leurs produits de sport. Ils en profitent pour placer leur propres publicités en bas de page.

![Formulaire de création](img/5_4.png)

### [Runtastic](www.runtastic.com)

Runtastic est aussi un site qui accompagne les sportifs durant leurs entrainements. Il est beaucoup utilisé par les amateurs. C'est parce que le site est plus poussé au niveau de l'accompagnement et la motivation que sur l'analyse des entrainements (ils proposent aussi une analyse des performances).

### [Openrunner](www.openrunner.com)

Openrunner est un site d'organisation de randonnées/trails. Il cible surtout les personnes pratiquant ce sport à la montagne. Car il propose de détailler les chemins et l'altitude avec une précision extrême. 

### [CalculItinéraires](www.calculitineraires.fr)

CalculItinéraires est un site spécialisé sur la création de tracés. Ils mettent à disposition des utilisateurs un nombre de fonctions impréssionnant. Comme par exemple, la possibilité de changer de map (passer de Google map à Open Street Map). Il y a aussi beaucoup d'informations sur les tracés créés; outre l'élévation ils proposent de calculer les calories brulées, le temps en fonction de l'allure,… 

Je ne prévois pas de donner autant d'informations sur les tracés.

## Conclusion

Tous ces sites ont des qualités et des défaults. Après avoir longtemps parcouru chaqun, j'ai pu créer une liste des points forts et une des erreurs à éviter. Cette liste m'a guidé dans mon travail et m'a permis d'éviter les erreurs avant de les commetre. 

### Points forts à retenir

-	Accompagner les nouveaux utilisateurs lors la création de tracé.
-	Rendre la création de tracé la plus simple possible.
-	Pouvoir changer le fond de la map.
-	Insiter les utilisateurs à faire des actions.
-	Interface simple et intuitive.
-	Garder en mémoire le tracé créé.

### Erreurs à éviter

-	Demander trop d'informations d'un coup aux utilisateurs (long formulaires).
-	Créer des interfaces complexes.

Après l'observations de tous ces sites j'ai pu me lancer dans la conception de l'interface avec une idée clair vers quoi me diriger.

# 10.Technologies du site

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
