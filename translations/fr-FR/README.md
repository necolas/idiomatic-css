# Principes d'écriture pour des CSS cohérents et idiomatiques

Le présent document liste des recommandations raisonnables pour le développement CSS.

Il n'est pas destiné à être normatif et je ne souhaite pas imposer mes préférences en matière de code à tout le monde. Toutefois, ces lignes directrices encouragent fortement l'utilisation de conventions existantes, communes et judicieuses.

Ceci est un document évolutif et les nouvelles idées sont toujours les bienvenues.

Merci de bien vouloir contribuer.

[Document original en anglais](https://github.com/necolas/idiomatic-css/)

## Table des matières

1. [Principes généraux](#principes-generaux)
2. [Indentation](#indentation)
3. [Commentaires](#commentaires)
4. [Format](#format)
5. [Nommage](#nommage)
6. [Exemple pratique](#exemple)
7. [Organisation](#organisation)
8. [Compilation et déploiement](#compilation-et-deploiement)

[Remerciements](#remerciements)

<a name="principes-generaux"></a>
## 1. Principes généraux

> Une des clefs d'une bonne gestion de projet est de réaliser qu'écrire du code pour soi-même est une mauvaise idée™. Si des milliers de personnes sont amenées à utiliser votre code, alors écrivez votre code en visant un maximum de clarté, et non en fonction de croyances personnelles comme la lecture de spécifications qui rendrait plus intelligent." - Idan Gazit

* Tout code présent dans n'importe quelle base de code doit avoir l'air d'avoir été écrit par une seule personne, peu importe le nombre de gens qui y ont contribué,
* Appliquez les conventions de style de manière stricte,
* En cas de doute, utilisez des conventions existantes et communes.

<a name="indentation"></a>
## 2. Indentation

Une seule manière d‘indenter devrait être utilisée sur l'ensemble du code source de votre projet. Soyez toujours constant dans votre façon d‘indenter. Utilisez des espaces pour améliorer la lisibilité.

* Ne mélangez _jamais_ les espaces et les tabulations pour l'indentation.
* Choisissez entre des espaces ou de vraies tabulations. Tenez-vous en à votre choix sans y déroger. (Préference : espaces)
* Si vous utilisez les espaces, choisissez le nombre de caractères utilisé pour chaque niveau d'indentation. (Préference : 4 espaces)

Astuce : Configurez votre éditeur afin qu'il affiche les "caractères invisibles". Cela vous permettra de supprimer les espaces en fin de ligne, les espaces dans les lignes vides et évitera de polluer vos commits.

<a name="commentaires"></a>
## 3. Commentaires

Bien commenter son code est extrêmement important. Prenez le temps de décrire les composants, comment ils fonctionnent, leurs limites, et la manière dont ils sont conçus. Ne laissez pas les autres membres de l'équipe deviner le but d'un code inhabituel ou non trivial.

La façon de commenter doit être simple et similaire dans toute base de code.

* Placez les commentaires sur une nouvelle ligne au-dessus de leur sujet,
* Evitez les commentaires en fin de ligne,
* Gardez une longueur de ligne de taille raisonnable, par exemple 80 caractères,
* Utilisez les commentaires comme bon vous semble pour diviser le code CSS en parties distinctes,
* Rédigez vos commentaires avec des majuscules et des minuscules et gardez une indentation constante pour le texte.

Astuce: Paramètrez votre éditeur pour qu'il vous fournisse des raccourcis claviers qui produisent des commentaires conventionnels.

#### Exemple en CSS :

```css
/* ==========================================================================
   Bloc de commentaire de section
   ========================================================================== */

/* Bloc de commentaire de sous-section
   ========================================================================== */

/*
 * Groupe de bloc de commentaires.
 * Parfait pour les explications sur plusieurs lignes et la documentation.
 */

/* Commentaire simple */
```

#### SCSS exemple :

```scss
// ==========================================================================
// Bloc de commentaire de section
// ==========================================================================

// Bloc de commentaire de sous-section
// ==========================================================================

//
// Groupe de bloc de commentaires.
// Parfait pour les explications sur plusieurs lignes
// et la documentation

// Commentaire simple
```


<a name="format"></a>
## 4. Format

Le format de code choisi doit assurer: une bonne lisibilité, des commentaires clairs, une réduction des probabilités d'insertion accidentelle d'erreurs, et la production de fichiers diff et de résolution des problèmes pratiques.

1. Un seul sélecteur par ligne dans les régles à plusieurs sélecteurs,
2. Un espace avant l'accolade ouvrante d'une règle,
3. Une déclaration par ligne dans un bloc de déclarations,
5. Un espace après les deux points d'une déclaration,
6. Ajoutez toujours un point-virgule à la fin de la dernière déclaration d’un bloc,
7. Fermez l'accolade d'une règle au même niveau que le premier caractère de la règle,
8. Sautez une ligne entre chaque règle.

```css
.selecteur-1,
.selecteur-2,
.selecteur-3 {
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    display: block;
    color: #333;
    background: #fff;
}
```

#### Ordre des déclarations

L'ordre des déclarations doit toujours obéir à la même règle. Je préfère regrouper les règles connexes ensemble et déclarer les propriétés importantes relatives à la structure (c-à-d le positionnement et le modèle de boîte) avant les règles typographiques, l'arrière-plan et les couleurs.

```css
.selecteur {
    position: relative;
    display: block;
    width: 50%;
    height: 100px;
    padding: 10px;
    border: 0;
    margin: 10px;
    color: #fff
    background: #000;
}
```

L'ordre alphabétique est également très utilisé, mais le problème est qu'il sépare les propriétés liées. Par exemple, les décalages de positionnement ne sont plus regroupés ensemble et les propriétés du modèle de boîte se retrouvent éparpillées dans le bloc de déclaration.

#### Exceptions et légèrs écarts

De gros blocs de déclarations uniques peuvent utiliser un format légèrement différent, regroupées sur une seule ligne. Dans ce cas, il faut insérer un espace après l'accolade ouvrante et avant l'accolade fermante.

```css
.selecteur-1 { width: 10%; }
.selecteur-2 { width: 20%; }
.selecteur-3 { width: 30%; }
```

Les longues valeurs de propriétés, séparées par des virgules - comme des ensembles de dégradés et d'ombres - peuvent être agencées sur plusieurs lignes de manière à améliorer la lisibilité et produire des fichiers diff plus utiles. Divers formats peuvent alors être utilisés comme le montre l'exemple donné ci-dessous :

```css
.selecteur {
    box-shadow:
        1px 1px 1px #000,
        2px 2px 1px 1px #ccc inset;
    background-image:
        linear-gradient(#fff, #ccc),
        linear-gradient(#f3c, #4ec);
}
```

#### Divers

* Utilisez des minuscules pour les valeurs hexadécimales, exemple : `#aaa`,
* Utilisez toujours le même type de guillemets. Ma préférence va aux doubles guillemets, exemple : `content: ""`,
* Utilisez toujours des guillemets pour les valeurs dans les sélecteurs, exemple :  `input[type="checkout"]`,
* _Lorsque c'est autorisé_, évitez de spécifier les unités pour les valeurs nulles, exemple : `margin: 0`.

### Préprocesseurs: considérations additionnelles pour le formatage

Les différents préprocesseurs CSS offrent des possibilités, des fonctionnalités et une syntaxe différentes. Vos conventions doivent être étendues pour s'adapter aux particularités des préprocesseurs que vous utilisez. Les conventions suivantes font référence à Sass.

* Limiter l'imbrication à un niveau de profondeur. Réexaminez toute imbrication supérieure à deux niveaux de profondeur.
Cela évite des sélecteurs CSS trop spécifiques,
* Evitez d'imbriquer un trop grand nombre de règles, séparez les lorsque cela nuit à la lisibilité. Je préfère éviter les imbrications qui dépassent les 20 lignes,
* Placez toujours les déclarations "@extend" en début de bloc,
* Si possible, regroupez toutes les déclarations "@include" en début de bloc juste après les déclarations "@extend",
* Pensez à préfixer vos propres fonctions avec `x-` ou un autre espace de nom. Cela permet d'éviter potentiellement de confondre votre fonction avec une fonction native CSS, ou les conflits avec des fonctions provenant de bibliothèques.

```scss
.selecteur-1 {
    @extend .other-rule;
    @include clearfix();
    @include box-sizing(border-box);
    width: x-grid-unit(1);
    // other declarations
}
```


<a name="nommage"></a>
## 5. Nommage

Vous n'êtes pas un compilateur/compresseur de code humain, alors ne prétendez pas en être un.

Utilisez des noms clairs et réfléchis pour les classes HTML. Choisissez un modèle de nommage cohérent et compréhensif qui a du sens à la fois dans les fichiers HTML et dans les fichiers CSS.

```css
/* Exemple de code mal nommé */

.s-scr {
    overflow: auto;
}

.cb {
    background: #000;
}

/* Exemple de code bien nommé */

.is-scrollable {
    overflow: auto;
}

.column-body {
    background: #000;
}
```


<a name="exemple"></a>
## 6. Exemple pratique

Un exemple de divers conventions.

```css
/* ==========================================================================
   Construction de la grille
   ========================================================================== */

/*
 * Exemple de code HTML:
 *
 * <div class="grid">
 *     <div class="cell cell-5"></div>
 *     <div class="cell cell-5"></div>
 * </div>
 */

.grid {
    overflow: visible;
    height: 100%;
    /* Évite d'entourer les cellules avec un inline-block */
    white-space: nowrap;
    /* Suppression des espaces entre les cellules */
    font-size: 0;
}

.cell {
    box-sizing: border-box;
    position: relative;
    overflow: hidden;
    width: 20%;
    height: 100%;
    /* Définition de l'espacement entre les cellules */
    padding: 0 10px;
    border: 2px solid #333;
    vertical-align: top;
    /* Réinitialisation de la gestion des espaces */
    white-space: normal;
    /* Réinitialisation de la taille de police */
    font-size: 16px;
}

/* Etats des cellules */

.cell.is-animating {
    background-color: #fffdec;
}

/* Dimensions des cellules
   ========================================================================== */

.cell-1 { width: 10%; }
.cell-2 { width: 20%; }
.cell-3 { width: 30%; }
.cell-4 { width: 40%; }
.cell-5 { width: 50%; }

/* Styles de cellule
   ========================================================================== */

.cell--detail,
.cell--important {
    border-width: 4px;
}
```


<a name="organisation"></a>
## 7. Organisation

L'organisation du code est une partie importante de n'importe quelle base de code CSS et devient cruciale pour les grosses bases de code.

* Séparez de manière logique les différentes parties de code,
* Utilisez des fichiers distincts (concaténés au cours de l'étape de compilation) pour aider à découper le code en différents composants,
* Si vous utilisez un préprocesseur, stockez le code récurrent dans des variables pour la couleur, la typographie, etc.


<a name="compilation-et-deploiement"></a>
## 8. Compilation et déploiement

Les projets devraient toujours essayer de mentionner des façons génériques grâce auxquelles le code source peut être validé, testé, compressé et versionné en préparation à l'utilisation en production.
Pour cela, [grunt](https://github.com/cowboy/grunt) de Ben Alman est un excellent outil.


<a name="remerciements"></a>
## Remerciements

Merci à tous ceux qui ont contribué à [idiomatic.js](https://github.com/rwldrn/idiomatic.js). Cela a été une source d'inspiration, de citations et de conventions.
