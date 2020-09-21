# Pour l'évaluation

-   **Prendre 10 min à chaque fin de séance pour écrire ce qu'on a fait
    dans le fichier
    [./rapports_hebdomadaires.md](./rapports_hebdomadaires.md)**
-   le rapport terminal doit être rédiger en Latex dans le répertoire [./rapports](rapports)

# Modélisation de la propagation de potentiels d'action cardiaques

## Objectif final, très ambitieux.

On souhaite réaliser un simulateur la propagation des potentiels
d'action cardiaques dans un domaine Omega = (0,l1)x(0,l2)
[éventuellement aussi en 3D, (0,l1)x(0,l2)x(0,l3)]. On utilisera le
modèle dit monodomaine avec le modèle *minimal model* de [Bueno-Orovio
et al. 2008]. L'idée générale es d'essayer de reproduire les simulations
de l'article [Bueno-Orovio et al. 2008].

On utilisera une méthode de différences finies avec un schéma en temps issu de
l'article [Perego et Veneziani 2009].

## Première partie : recherche de resources, documentation

1.  L'équation modèle associée à ce problème est l'équation parabolique linéaire
    \(\partial_t u - \partial_x(a(x) \partial_x u) = f(t,x)\), avec un coefficient
    non constant \(a(x)\), mais régulier. Trouver et synthétiser de la
    documentation sur ce type d'équation. Quelles conditions aux limites peut on
    utiliser ? Quelles sont les conditions sur \(a(x)\) pour pouvoir la résoudre,
    etc ?
2.  Trouver de la documentation sur les méthodes de différences finis pour cette
    équation. Qu'est-ce qui se passe lorsque l'on est en dimension supérieure (2
    ou 3) et que le coefficient \(a(x)\) devient une matrice ?
3.  Détailler le système d'équation que l'on doit résoudre à chaque pas de temps,
    et les méthodes possibles pour le résoudre. Quelles sont les conséquences sur
    le stockage de la matrice en pratique ?

## Deuxième partie : programmation dans un cas simplifié

On s'intéresse au cas mono-dimensionnel (\(d=1\)) avec un coefficient \(a(x)=a\)
constant. L'objectif est de bien comprendre l'implémentation des méthodes, avant
de s'attaquer au problème complet.

1.  Détailler l'architecture du code à implémenter, en essayant d'avoir un code
    modulaire et extensible facilement. Entrées et sorties ? Structuration du
    code en fichiers ? Quels outils de l'ensemble scipy/numpy ?
2.  Dans le cas \(a(x)=1\), on retrouve l'équation de la chaleur. Déterminer des
    situations pour lesquelles on peut calculer des solutions analytiques. Nous
    les utiliserons pour valider notre implémentation.
3.  Programmer la résolution du problème dans le cas \(d=1\), et vérifier cette
    implémentation à l'aide des tests de la question 2.

## Troisième partie : le cas général

On va généraliser le code produit dans la partie précédente au cas non-linéaire
complet, c'est à dire avec le système d'équations différentielles de l'article
[Bueno-Orovio et al. 2008], et en dimension \(d=2\).

1.  Quelles sont les conséquences du passage à la dimension \(d=2\) sur le système
    linéaire à résoudre à chaque pas de temps ? Sur l'algorithme utilisé pour le
    résoudre ? On suppose toujours ici que le problème est linéaire, \(f:=f(t,x)\).
2.  Comment pourrait-on trouver des solutions analytiques permettant de valider
    l'implémentation, dans le cas linéaire ?
3.  Qu'est-ce qui doit changer dans le code pour pouvoir coupler l'équation avec
    le système d'équations différentielle (cas \(f:=f(t,u...)\)) ?
4.  Produire le code de résolution du problème et le tester, d'abord en 2D
    linéaire, puis en 2D couplé avec le système d'EDO.

## refs

- livre de A. Tveito et R. Winther, disponible en ligne via Babord+
  https://babordplus.hosted.exlibrisgroup.com/permalink/f/165335h/TN_springer_s3-540-26740-9_47993
- À compléter dans le répertoire [./refs](./refs)
