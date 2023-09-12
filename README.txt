Ce projet a pour but de mettre en place un modèle d'apprentissage permettant de prédire avec une précision satisfaisante l'issue d'une partie de League Of Legends à partir uniquement de l'information de la sélection des champions.

Il se découpe en plusieurs parties :

  - La récuppération des matchs via l'API officielle de RIOT GAMES. Pour cela, nous devons dans un premier temps récupperer les noms des joueurs possédants les plus hauts rangs (via le fichier fetchNAMES). Ensuite, nous devons convertir ces noms en PUUIDS (id unique 
    à travers le monde) via les fichiers XX_fetchPUUIDS, et enfin regrouper les matchs que ces personnes ont joué dernièrement. L'API possède une limite de requête par minute assez faible, mais nous permet de faire en parallèle des requêtes en europe (EU), en amérique
    (NA) et en corée du sud (KR), ce qui nous permet de récolter assez de données.

  - Après ce tunnel de réccupération de donnée, nous disposons dans le répertoire MATCHDATA un ensemble de matchs, représentés par la selection des champions pour chaque équipe et l'équipe victorieuse.

  - Une partie cruciale de ce projet est la vectorisation des champions. En effet, nous ne pouvons pas donner en entrée simplement le nom d'un champions. Nous devons donc trouver un moyen de le convertir en un vecteur transportant l'information du caractère du champions 
    (forces, faiblesses, style, ...). Cela est fait dans le fichier championSpace, mais une seconde itération afin d'affiner cette vectorisation est nécéssaire.

  - Nous convertissons ensuite nos données contenues dans le répertoire MATCHDATA en information lisible par les modèles d'apprentissage, en utilisant principalement la vectorisation mise en place précédemment. Cela est fait dans le fichier Make_X_Y.

  - Les modèles d'IA sont résumés dans le fichier BouleDeCristal, et sont pour l'instant uniquement des simples tests, la vectorisation n'étant pas assez poussée pour avoir des résultats convaincants.



Le projet est réalisé avec Python 3.9.7, et tensorflow version: 2.10.0, numpy version: 1.20.3, pandas version: 1.3.4, scikit-learn version: 0.24.2
