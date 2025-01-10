## Introduction



### Présentation du projet - Analyse de la qualité du vin rouge

Dans le code deux modèles ont été supprimé car il bloqué le téléchargement des données Dans le cadre de ce projet, nous avons exploité un jeu de données portant sur la qualité du vin rouge au Portugal. Ce jeu de données comporte 12 variables, parmi lesquelles une variable cible représentant la qualité du vin, évaluée sur une échelle de 0 à 9, et 1 variables explicatives comme l'acide citrique ou le pH. Il regroupe les informations de 1 599 échantillons de vin. L'objectif principal de ce projet est d'appliquer diverses méthodes d'apprentissage de réduction de dimensionnalité pour analyser et modéliser les relations entre ces variables et la qualité du vin.

#### Présentation du jeu de données

Le jeu de données étudié propose une description détaillée de la qualité du vin rouge, basée sur 11 variables explicatives. Ces dernières incluent des paramètres physico-chimiques tels que l'acidité fixe, l'acidité volatile, la teneur en acide citrique, le sucre résiduel, le taux de chlorures, ainsi que des mesures relatives au dioxyde de soufre (libre et total). D'autres caractéristiques, comme la densité, le pH, les sulfates, et la concentration en alcool, sont également présentes. Enfin, une colonne intitulée "quality" reflète l'évaluation de la qualité globale du vin, réalisée par des experts. Ce jeu de données constitue une base solide pour examiner les interactions entre ces variables et prédire la qualité du vin.
Les différentes variables du jeu de données sont :

- fixed acidity : Mesure de l'acidité fixe, composée principalement d'acides non volatils comme l'acide tartrique, exprimée en g/dm'.
- volatile acidity : Quantité d'acidité volatile, principalement due à l'acide acétique, exprimée en g/dm'
- citric acid : Concentration d'acide citrique, qui apporte fraîcheur et saveur au vin, exprimée en g/dm'
- residual sugar : Quantité de sucre restant après la fermentation, exprimée en g/dm'.
  chlorides : Concentration en chlorures (sels), indicateur de la salinité, exprimée en g/dm'.
- free sulfur dioxide : Niveau de dioxyde de soufre libre, utilisé comme antioxydant et agent antimicrobien, exprimé en mg/dm'
- total sulfur dioxide : Quantité totale de dioxyde de soufre, incluant les formes libres et liées,exprimée en mg/dm'
- density : Densité du vin, liée à sa teneur en sucre et en alcool, exprimée en g/cm'.
  pH : Mesure de l'acidité ou de l'alcalinité du vin.
- sulphates : Teneur en sulfates, contribuant à un goût amer ou astringent, exprimée en g/dm'.
- alcohol : Pourcentage volumique d'alcool présent dans le vin (% vol).



#### Méthodes de réduction de dimensionnalité appliquées

Pour explorer et comprendre les relations complexes entre les variables explicatives et la qualité du vin, nous avons employé diverses méthodes de réduction de dimensionnalité. Ces techniques, telles que l'Isomap, le Locally Linear Embedding (LLE), le Modified LLE, le Spectral Embbedding, le Multidimensional Scaling (MDS), et le t-SNE, permettent de simplifier la représentation des données tout en conservant les structures essentielles. Elles offrent des outils puissants pour visualiser et analyser les relations multidimensionnelles sous-jacentes, facilitant ainsi l'identification des tendances et des regroupements.



### Présentation des méthodes de réduction de dimensionnalité :

#### Présentation de la méthode ISOMAP

Isomap (pour Isometric Mapping) est une technique de réduction de dimensionnalité qui transforme des données issues d'un espace de haute dimension en un espace de dimension inférieure, tout en préservant leur structure géométrique globale. Cette méthode repose sur l'hypothèse que les données résident sur une variété (manifold) non linéaire et conserve les distances géodésiques, c'est-à-dire les distances mesurées le long de la variété, plutôt que les distances euclidiennes classiques.

Après application d'Isomap, les données sont projetées dans un espace de dimension réduite (souvent en 2D ou 3D). Dans ce nouvel espace, leurs coordonnées reflètent la structure géométrique globale des données initiales. Par exemple, dans le graphique obtenu, les points correspondant à la qualité du vin sont redistribués dans un espace bidimensionnel tout en préservant les relations de similarité entre les échantillons.



##### Nouvelle représentation des données

L'application d'Isomap attribue à chaque point du jeu de données de nouvelles coordonnées dans l'espace de dimension réduite. Ces coordonnées, distinctes des dimensions initiales, représentent les relations géométriques globales au sein de la variété sous-jacente. Dans le graphique généré, chaque point est positionné dans cet espace réduit, les nouvelles coordonnées résultant de l'optimisation effectuée par la méthode Isomap.

##### Problème d'optimisation résolu par Isomap

Isomap procède en trois étapes principales pour réaliser la réduction de dimensionnalité :

1. ﻿﻿﻿Construction d'un graphe de voisinage
    Isomap commence par connecter chaque point à ses k plus proches voisins en utilisant la distance euclidienne dans l'espace initial.
2. ﻿﻿﻿Calcul des distances géodésiques
    Les distances géodésiques entre les points sont estimées en déterminant le plus court chemin dans le graphe, à l'aide d'algorithmes comme Floyd-Warshall ou Dijkstra.
3. ﻿﻿﻿Réduction de dimension par décomposition spectrale
    La matrice des distances géodésiques est utilisée pour effectuer une analyse en composantes principales (ACP). Cette étape permet de calculer les coordonnées des points dans l'espace de dimension réduite grâce à une décomposition spectrale.

L'objectif global est de minimiser la distorsion des distances géodésiques entre les points, afin de garantir que la structure géométrique globale des données soit fidèlement représentée dans l'espace réduit.

#### Résolution du problème d'optimisation

Pour résoudre ce problème, Isomap s'appuie sur une décomposition spectrale de la matrice des distances géodésiques. Cette technique consiste à calculer les vecteurs propres et les valeurs propres de cette matrice, ce qui permet de déterminer les nouvelles coordonnées des points. Ces étapes reposent sur des outils mathématiques bien établis en algèbre linéaire, garantissant ainsi une solution efficace et stable.

#### Limitations et garanties sur l'optimalité

Bien qu'efficace, Isomap présente certaines limitations :

- ﻿﻿Construction du graphe de voisinage: Si le nombre de voisins (k) est mal choisi, la structure géométrique des données peut être mal représentée.
- ﻿﻿Calcul des distances géodésiques: Les approximations introduites par les algorithmes de plus court chemin peuvent affecter la qualité des résultats.
- ﻿﻿Complexité des données: Pour des données bruitées ou avec des structures complexes,
- Isomap peut avoir du mal à capturer correctement la variété sous-jacente.

Cependant, lorsque les données sont bien structurées et que les paramètres sont ajustés de manière optimale, Isomap fournit des résultats robustes, proches d'une minimisation globale.

#### Conclusion

Le graphique obtenu avec Isomap illustre comment cette méthode réduit les données sur la qualité du vin dans un espace bidimensionnel. Les points sont organisés de manière à préserver les relations géométriques globales, ce qui permet de visualiser des groupes ou des similarités entre les échantillons. Les nouvelles coordonnées sont issues de la décomposition spectrale appliquée sur les distances géodésiques. Bien que la minimisation globale ne soit pas strictement garantie, Isomap est particulièrement adapté aux cas où les données présentent une structure géométrique claire.



### Méthode Locally Linear Embedding (LLE)

#### Présentation de la méthode

Après l'application de LLE, chaque donnée est projetée dans un espace de dimension réduite (dans cet exemple, en 2D). Les nouvelles coordonnées ne correspondent plus directement aux variables d'origine, mais décrivent la position relative des points, en tenant compte de leurs relations locales.

Sur le graphique généré, ces nouvelles coordonnées permettent une visualisation simplifiée tout en conservant les relations locales importantes. Cela facilite l'interprétation visuelle des regroupements potentiels ou des structures sous-jacentes dans les données.

#### Nouvelle représentation des données

Après l'application de LLE, chaque point du jeu de données se voit attribuer de nouvelles coordonnées dans un espace de dimension réduite (ici, en 2 dimensions). Ces nouvelles coordonnées ne sont plus basées sur les variables initiales, mais elles représentent la position relative des points en tenant compte des relations locales entre eux.

Dans le graphique, ces nouvelles coordonnées permettent de représenter visuellement les relations entre les échantillons, tout en simplifiant leur compréhension et en mettant en évidence des regroupements potentiels.

#### Problème d'optimisation résolu par LLE

LLE vise à conserver, dans l'espace réduit, les mêmes relations locales qu'il y avait dans l'espace d'origine. Pour cela, la méthode procède comme suit :

- ﻿﻿Identification des voisins proches : Chaque point est analysé pour identifier un groupe de voisins proches basés sur leur proximité dans l'espace d'origine.
- ﻿﻿Représentation locale : Chaque point est approximé comme une combinaison linéaire de ses voisins.
- ﻿﻿Projection globale : Les données sont projetées dans un espace de dimension réduite tout en respectant les relations locales identifiées dans les étapes précédentes.

L'objectif principal est de conserver les liens et la structure locale des données tout au long du processus de réduction.

#### Résolution du problème d'optimisation

La réduction par LLE se déroule en deux étapes principales :

- ﻿﻿Représentation locale : Pour chaque point, les relations avec ses voisins sont modélisées en analysant leur proximité dans l'espace initial.
- ﻿﻿Projection dans l'espace réduit : Les positions des points dans l'espace réduit sont calculées de manière à préserver ces relations locales. Cette étape utilise des outils mathématiques avancés pour garantir que la structure locale des données reste intacte.

#### Limitations et garanties sur l'optimalité

Bien que LLE soit une méthode robuste pour des données bien structurées, elle ne garantit pas une solution optimale dans tous les cas. La qualité des résultats dépend de plusieurs facteurs :

- ﻿﻿Nombre de voisins: Si le paramètre fixant le nombre de voisins est mal ajusté, les relations locales peuvent être mal représentées.
- ﻿﻿Complexité des données: Si les données sont fortement bruitées ou ne présentent pas de structure claire, la représentation finale peut être peu significative.

Malgré ces limitations, pour des données bien préparées et des paramètres bien choisis, LLE permet de produire des représentations fiables et utiles pour l'analyse exploratoire.

#### Conclusion

Dans le graphique généré, LLE a permis de réduire les données sur la qualité du vin à deux dimensions tout en préservant les relations locales entre les échantillons. Les points proches dans l'espace d'origine restent proches dans l'espace réduit, montrant ainsi que la méthode a bien préservé la structure locale des données. Cette représentation simplifiée facilite l'interprétation et permet d'identifier des regroupements ou des patterns significatifs au sein des données.

### Méthode Modified Locally Linear Embedding (Modified LLE)

#### Présentation de la méthode

La méthode Modified LLE (Modified Locally Linear Embedding) vise, comme la méthode standard LLE, à réduire la dimensionnalité des données tout en préservant leurs relations locales. Cependant, elle diffère en apportant des ajustements pour améliorer la stabilité et la précision, en particulier lorsque les données suivent une structure proche d'un alignement linéaire.

Cette méthode réorganise les données dans un espace de dimension réduite (ici 2D), tout en préservant leurs relations locales. Les ajustements mathématiques qu'elle introduit permettent de réduire les risques d'écrasement ou d'interférence entre les points lors de la projection.

Dans le graphique généré, les points forment une structure en arc qui reflète comment les relations locales ont été préservées dans l'espace réduit.

#### Nouvelle représentation des données

Après l'application de la méthode Modified LLE, chaque point a de nouvelles coordonnées dans l'espace réduit. Ces nouvelles coordonnées permettent de visualiser la structure locale des données dans un espace simplifié tout en conservant les proximités entre les points.

Dans le graphique, ces nouvelles coordonnées montrent une organisation claire des données, les points étant disposés de manière continue et ordonnée, tout en respectant les relations locales issues de l'espace d'origine.

#### Problème d'optimisation résolu par Modified LLE

La méthode Modified LE repose sur les principes fondamentaux de LL.E classique, avec des ajustements pour résoudre certains problèmes de stabilité. Le problème d'optimisation peut être décrit comme suit :

- ﻿﻿Identification des relations locales : Un voisinage est défini pour chaque point en fonction de ses voisins les plus proches dans l'espace d'origine.
- ﻿﻿Projection réduite : Les données sont projetées dans l'espace réduit tout en minimisant les distorsions des relations locales.
- ﻿﻿Ajustements supplémentaires : La version modifiée inclut des mécanismes qui renforcent la précision des projections pour éviter des ambiguïtés ou des regroupements erronés.

#### Résolution du problème d'optimisation

Modified ILE suit un processus similaire à celui de LLE classique, avec des modifications pour garantir une meilleure stabilité :

- ﻿﻿Identification des voisins proches : Chaque point est analysé pour déterminer ses relations avec les points les plus proches dans l'espace d'origine.
- ﻿﻿Projection stabilisée : Une optimisation est réalisée pour minimiser les distorsions dans l'espace réduit. Ces ajustements permettent de réduire les erreurs liées à des alignements complexes ou des structures bruitées.

#### Limitations et garanties sur l'optimalité

Comme pour la méthode LLE classique, il n'y a pas de garantie d'atteindre une minimisation globale parfaite. Cependant, la version modifiée est conçue pour améliorer les performances, notamment sur des données complexes ou bruitées. La qualité des résultats dépend toujours des éléments suivants :

- ﻿﻿Nombre de voisins: Un choix inadapté peut entraîner une mauvaise représentation des relations locales.
- ﻿﻿Structure des données: Les données très complexes ou bruitées peuvent perturber les projections.

Malgré cela, dans le cas du graphique généré, la structure en arc montre que la méthode a bien capturé la structure locale, ce qui reflète son efficacité dans ce contexte.

#### Conclusion

Le graphique montre que la méthode Modified ILE a réduit les données sur la qualité du vin tout en respectant leur structure locale. Cette représentation simplifiée, en arc, résulte d'une optimisation efficace qui préserve les relations locales tout en améliorant la stabilité par rapport à LLE classique.

Cette méthode est particulièrement adaptée pour analyser des données présentant des relations linéaires ou complexes dans l'espace d'origine.



### Méthode Spectral Embedding

#### Présentation de la méthode

La méthode Spectral Embedding est une technique de réduction de dimensionnalité qui s'appuie sur les propriétés spectrales des graphes construits à partir des données. En exploitant la décomposition en valeurs propres d'une matrice issue des distances ou similarités entre les points, cette approche permet de projeter les données dans un espace de dimension réduite. L'objectif de Spectral Embedding est de préserver les relations locales et globales des données en exploitant la structure du graphe. Contrairement à des méthodes comme f-SNE ou Isomap, cette technique met l'accent sur les caractéristiques spectrales pour générer une représentation simplifiée des données. Dans l'espace réduit, les données sont projetées de manière à former, par exemple, une courbe en forme de "U", comme observé dans le graphique généré. Cette représentation reflète des relations sous-jacentes présentes dans l'espace d'origine.

#### Nouvelle représentation des données

Après l'application de la méthode, chaque point se voit attribuer de nouvelles coordonnées dans un espace à dimension réduite. Ces coordonnées sont dérivées des vecteurs propres associés à une matrice liée au graphe de similarité. Dans la nouvelle représentation, les points sont organisés de façon à préserver les relations globales et locales issues de l'espace d'origine. Cela permet une meilleure compréhension des liens entre les échantillons, tout en simplifiant leur visualisation et leur analyse.

#### Problème d'optimisation résolu par Spectral Embedding

La méthode Spectral Embedding vise à minimiser une fonction objective qui s'appuie sur les distances ou les similarités entre les points. Les étapes clés sont les suivantes :

1. Construction du graphe de similarité :

- ﻿﻿Un graphe est créé pour représenter les relations entre les points selon leur proximité.
- ﻿﻿Ce graphe peut être construit à l'aide du graphe des k plus proches voisins ou d'une fonction de similarité pondérée.
- Calcul de la matrice laplacienne normalisée :

• Une matrice qui représente le graphe est dérivée (souvent une matrice laplacienne normalisée).

3. Décomposition spectrale :

• Les vecteurs propres associés aux plus petites valeurs propres de cette matrice sont utilisés pour définir les nouvelles coordonnées des points.

L'objectif final est de projeter les données tout en conservant la structure intrinsèque du graphe dans l'espace réduit.

#### Résolution du problème d'optimisation

Pour résoudre ce problème, Spectral Embedding suit les étapes suivantes : 1. Calcul de la matrice de similarité : Une matrice est calculée pour capturer les relations entre les points. 2.

Décomposition spectrale : Une décomposition en valeurs propres de la matrice laplacienne est effectuée. Les vecteurs propres associés aux plus petites valeurs propres sont sélectionnés. 3.

Projection finale : Les points sont projetés dans l'espace réduit à l'aide des coordonnées dérivées des vecteurs propres.

#### Limitations et garanties sur l'optimalité

Bien que Spectral Embedding soit une méthode efficace, elle présente certaines limites : Qualité du graphe : Les résultats dépendent fortement de la construction initiale du graphe, notamment du choix du nombre de voisins. Sensibilité au bruit : Les données bruitées peuvent affecter la qualité de la représentation. Complexité computationnelle : La décomposition spectrale peut être coûteuse pour de très grands ensembles de données. Cependant, pour des données bien structurées, Spectral Embedding produit des représentations fiables et utiles.

#### Conclusion

Spectral Embedding a permis de projeter les données dans un espace réduit, révélant une structure en forme de "U" qui reflète les relations locales et globales des données initiales. En exploitant les propriétés spectrales des graphes, cette méthode s'avère particulièrement adaptée pour identifier des motifs ou des regroupements, tout en simplifiant l'analyse dans un espace de plus petite dimension.

### Multidimensional Scaling (MDS)

#### Présentation de la méthode

La méthode MDS est une technique de réduction de dimensionnalité qui transforme les données d'un espace initial (souvent de haute dimension) vers un espace de dimension plus réduite, tout en conservant les distances entre les points.

MDS ajuste la position des points dans l'espace réduit (ici 2D) de manière à ce que les distances entre eux soient aussi proches que possible des distances dans l'espace d'origine. Contrairement à LE ou Isomap, qui se concentrent sur les relations locales ou géodésiques, MDS vise à conserver directement les distances euclidiennes globales.

Dans le graphique généré, les points représentant la qualité du vin sont répartis de manière à refléter leurs relations de similarité basées sur leurs distances globales.

#### Nouvelle représentation des données

Après l'application de MDS, chaque point du jeu de données se voit attribuer de nouvelles coordonnées dans un espace 2D. Ces coordonnées ne sont plus liées aux dimensions initiales des données, mais elles respectent les distances calculées dans l'espace d'origine.

Dans le graphique, les nouvelles coordonnées montrent une distribution qui capture les relations globales entre les échantillons, permettant de visualiser leur organisation et leurs similitudes.

#### Problème d'optimisation résolu par MDS

La méthode MDS cherche à minimiser la différence entre les distances calculées dans l'espace réduit et les distances dans l'espace d'origine. Cela revient à résoudre un problème d'optimisation où l'objectif est de réduire cette distorsion globale des distances.

En d'autres termes, MDS ajuste la position des points dans l'espace réduit pour que les distances soient les plus proches possible de celles mesurées dans l'espace d'origine.

#### Résolution du problème d'optimisation

La méthode MDS utilise un algorithme itératif pour résoudre ce problème :

- ﻿﻿Estimation initiale : Une configuration initiale des coordonnées des points dans l'espace réduit est générée.
- ﻿﻿Ajustements itératifs: Les positions des points sont progressivement modifiées pour minimiser les différences entre les distances dans l'espace réduit et celles dans l'espace d'origine.
- ﻿﻿Critère d'arrêt : Le processus se poursuit jusqu'à ce que les ajustements deviennent négligeables ou qu'un seuil défini soit atteint.

#### Limitations et garanties sur l'optimalité

La méthode MDS ne garantit pas une minimisation globale parfaite, notamment pour des jeux de données complexes. Plusieurs facteurs influencent les résultats :

- ﻿﻿Configuration initiale des points : Une mauvaise initialisation peut affecter le résultat final.
- ﻿﻿Complexité des données : Des distances globales très complexes ou bruitées peuvent entraîner des solutions sous-optimales.

Cependant, MDS produit généralement des représentations fiables qui approchent une solution optimale pour des données bien structurées.

#### Conclusion

Le graphique montre que MDS a transformé les données sur la qualité du vin en une représentation 2D tout en préservant les distances globales entre les échantillons. Cette représentation permet de visualiser des regroupements ou des relations globales entre les points, ce qui facilite l'analyse des similitudes ou des différences dans les données. MDS s'avère être une méthode adaptée pour analyser des relations générales entre des échantillons dans un espace simplifié.

### T-SNE

#### Présentation de la méthode

La méthode t-SNE (t-Distributed Stochastic Neighbor Embedding) est une technique non linéaire de réduction de dimensionnalité qui projette les données dans un espace de dimension réduite (souvent en 2D ou 3D), tout en conservant les relations locales entre les points.

t-SNE modifie la position des points de manière à ce que les points proches dans l'espace d'origine restent proches dans l'espace réduit. Contrairement à MDS ou Isomap, qui cherchent à préserver des distances globales, t-SNE se concentre presque exclusivement sur les relations locales, ce qui permet de visualiser des clusters ou des groupes similaires.

Dans le graphique généré, t-SNE a réorganisé les données de manière à faire apparaître une structure en deux branches principales, reflétant probablement des relations locales fortes présentes dans les données d'origine.

#### Nouvelle représentation des données

Après l'application de t-SNE, chaque point du jeu de données se voit attribuer de nouvelles coordonnées dans un espace réduit. Ces coordonnées ne sont plus directement basées sur les dimensions d'origine, mais elles reflètent la proximité locale entre les points.

Dans le graphique, les données sont réparties selon une structure 2D, où les points proches indiquent des échantillons similaires en termes de caractéristiques. Cette représentation simplifiée est particulièrement utile pour identifier des regroupements ou des patrons cachés dans les données.

#### Problème d'optimisation résolu par t-SNE

t-SNE résout un problème d'optimisation basé sur une probabilité de similarité entre les points :

- ﻿﻿Dans l'espace d'origine : La méthode calcule une probabilité reflétant la similarité entre deux points, basée sur leur distance. Cette probabilité suit une distribution gaussienne.
- ﻿﻿Dans l'espace réduit : Une probabilité similaire est calculée, mais elle suit une distribution t de Student, qui est plus adaptée pour capturer les relations locales.
- ﻿﻿Objectif: Minimiser la différence (ou divergence) entre les deux distributions de probabilités en ajustant les positions des points dans l'espace réduit.

#### Résolution du problème d'optimisation

La méthode t-SNE utilise une optimisation itérative appelée descente de gradient :

- ﻿﻿Initialisation: Une configuration initiale aléatoire est générée pour les points dans l'espace réduit.
- ﻿﻿Ajustements: À chaque itération, les positions des points sont ajustées pour réduire la différence entre les distributions de probabilités dans les deux espaces.
- ﻿﻿Critère d'arrêt : Le processus se poursuit jusqu'à ce que les ajustements deviennent insignifiants ou qu'un nombre maximal d'itérations soit atteint.

#### Limitations et garanties sur l'optimalité

La méthode t-SNE ne garantit pas une solution optimale globale :

- ﻿﻿Dépendance à l'initialisation : Les résultats dépendent fortement de la configuration initiale des points.
- ﻿﻿Paramètres critiques : Le paramètre de perplexité, par exemple, joue un rôle important dans l'équilibre entre relations locales et globales.
- ﻿﻿Solutions variables : Étant donné que l'algorithme commence souvent avec une configuration aléatoire, les solutions obtenues peuvent varier légèrement d'une exécution à l'autre.

Cependant, dans la majorité des cas, t-SNE produit des représentations qualitativement utiles, particulièrement pour l'identification de clusters ou de regroupements.

#### Conclusion

Dans le graphique généré, t-SNE a organisé les données sur la qualité du vin dans un espace 2D en mettant en évidence des structures locales. Les deux branches visibles montrent que les données présentent des relations internes fortes, capturées efficacement par la méthode. Bien que les distances globales ne soient pas strictement respectées, cette visualisation est particulièrement utile pour explorer des regroupements ou des similarités entre les échantillons.





### Conclusion

L'analyse de la qualité du vin rouge à travers des méthodes de réduction de dimensionnalité a permis d'explorer les relations complexes entre ses caractéristiques physico-chimiques et sa qualité globale. Chaque technique a offert une perspective unique sur la structure des données :

- ﻿﻿Isomap et MDS ont mis en évidence des relations globales, facilitant l'identification de tendances générales.
- ﻿﻿LLE et Modified LLE ont permis de préserver et de visualiser les relations locales, particulièrement adaptées aux données présentant une structure complexe ou bruitée.
- ﻿﻿Enfin, t-SNE a révélé des regroupements locaux, mettant en lumière des similarités internes significatives entre les échantillons.

Ces représentations simplifiées ont non seulement permis une meilleure compréhension des données, mais aussi jeté les bases pour des analyses prédictives plus approfondies. Malgré les limitations spécifiques à chaque méthode, les résultats obtenus confirment l'intérêt d'explorer des approches non linéaires et géométriques pour le traitement de données multidimensionnelles.