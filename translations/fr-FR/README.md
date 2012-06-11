# Principes d'écriture de CSS consistent et idiomatique

Le présent document liste des recommandations raisonnables pour développer avec CSS.

Il n'est pas destiné à être normatif et je ne souhaite pas imposer mes préférences de style de code aux gens. Toutefois, ces lignes directrices encouragent fortement le fait d'utiliser des modèles existants, communs et sensés.

Ceci est un document évolutif et les nouvelles idées sont toujours les bienvenues. 
Merci de contribuer.

## Traductions

* [French] (https://github.com/necolas/idiomatic-css/tree/master/translations/fr-FR)
* [Italian](https://github.com/necolas/idiomatic-css/tree/master/translations/it-IT)
* [Serbian](https://github.com/necolas/idiomatic-css/tree/master/translations/sr)


## Table des matières

1. [Principes généraux](#principes-generaux)
2. [Espaces](#espaces)
3. [Commentaires](#commentaires)
4. [Format](#format)
5. [Nommage](#nommage)
6. [Exemple pratique](#exemple)
7. [Organisation](#organisation)
8. [ Compilation et déploiement ](# compilation-et-deploiement )

[Remerciements](# remerciements )


<a name="principes-generaux"></a>
## 1. Principes généraux

> "Part of being a good steward pour un projet réussi est de comprendre qu'écrire du code pour soi-même est une mauvaise idée™. Si des milliers de personnes utilisent votre code, alors écrivez votre code en visant une clarté maximale, et non en fonction de croyances personnelles comme comment devenir plus intelligent en lisant les specs." - Idan Gazit

* Tout code présent dans n'importe quelle base de code doit avoir l'air d'avoir été écrit par une seule personne, peu importe le nombre de gens qui y ont contribué.
* Appliquez les conventions de style de manière stricte.
* En cas de doute, utilisez des modèles existants et communs.


<a name="espaces"></a>
## 2. Espaces

Un seul style devrait exister pour la totalité du code source de votre projet.Soyez toujours consistant dans votre utilisation des espaces. Utilisez des espaces pour améliorer la lisibilité.

* Ne mélangez _jamais_ les espaces et les tabulations pour l'indentation.
* Choisissez entre des retraits (espaces) ou de vraies tabulations. Tenez vous en à votre choix sans y déroger. (Préference: espaces)
* Si vous utilisez les espaces, choisissez le nombre de caractères utilisés pour chaque niveau d‘indentation.
(Préference: 4 espaces)

Astuce: Configurez votre éditeur a fin qu'il affiche les "caractères invisibles". Cela vous permettra de supprimer les espaces en fin de ligne, et les lignes vides non intentionnelles et évitera de polluer vos soumissions.

<a name="commentaires"></a>
## 3. Commentaires

Bien commenter son code est important. Prenez le temps de décrire vos modules, comment ils fonctionnent, leurs limites, et la manière dont ils sont conçus. Ne laissez pas les autres membres de l'équipe deviner le but d'une partie inhabituelle de code difficile à comprendre.
Comment style should be simple and consistent within a single code base.

* Place comments on a new line above their subject.
* Evitez les commentaires en fin de ligne.
* Keep line-length to a sensible maximum, e.g., 80 columns.
* Make liberal use of comments to break CSS code into discrete sections.
* Use "sentence case" comments and consistent text indentation.

Tip: configure your editor to provide you with shortcuts to output agreed-upon
comment patterns.

#### Exemple en CSS :

```css
/* ==========================================================================
   Section de bloc de commentaires
   ========================================================================== */

/* Sous-section de bloc de commentaires
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
// Section de bloc de commentaires
// ==========================================================================

// Sous-section de bloc de commentaires
// ==========================================================================

//
// Groupe de bloc de commentaires.
// Parfait pour les explications sur plusieurs lignes 
// et la documentation

// Commentaire simple
```


<a name="format"></a>
## 4. Formatage

The chosen code format must ensure that code is: easy to read; easy to clearly
comment; minimizes the chance of accidentally introducing errors; and results
in useful diffs and blames.

1. One discrete selector per line in multi-selector rulesets.
2. A single space before the opening brace of a ruleset.
3. One declaration per line in a declaration block.
4. One level of indentation for each declaration.
5. A single space after the colon of a declaration.
6. Always include a semi-colon at the end of the last declaration in a
   declaration block.
7. Place the closing brace of a ruleset in the same column as the first
   character of the ruleset.
8. Separate each ruleset by a blank line.

```css
.selector-1,
.selector-2,
.selector-3 {
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    display: block;
    color: #333;
    background: #fff;
}
```

#### Ordre des déclarations

Declarations should be ordered in accordance with a single principle. My
preference is for related properties to be grouped together and for
structurally important properties (e.g. positioning and box-model) to be
declared prior to typographic, background, and color properties.

```css
.selector {
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

Alphabetical ordering is also popular, but the drawback is that it separates
related properties. For example, position offsets are no longer grouped
together and box-model properties can end up spread throughout a declaration
block.

#### Exceptions et légèrs écarts

Large blocks of single declarations can use a slightly different, single-line
format. In this case, a space should be included after the opening brace and
before the closing brace.

```css
.selector-1 { width: 10%; }
.selector-2 { width: 20%; }
.selector-3 { width: 30%; }
```

Long, comma separated property values - such as collections of gradients or
shadows - can be arranged across multiple lines in an effort to improve
readability and produce more useful diffs. There are various formats that could
be used; one example is shown below.

```css
.selector {
    box-shadow:
        1px 1px 1px #000,
        2px 2px 1px 1px #ccc inset;
    background-image:
        linear-gradient(#fff, #ccc),
        linear-gradient(#f3c, #4ec);
}
```

#### En vrac

* Use lowercase hex values, e.g., `#aaa`.
* Use single or double quotes consistently. Preference is for double quotes,
  e.g., `content: ""`.
* Always quote attribute values in selectors, e.g., `input[type="checkout"]`.
* _Where allowed_, avoid specifying units for zero-values, e.g., `margin: 0`.

### Pre processeurs: considérations additionnelles pour le format

Different CSS preprocessors have different features, functionality, and syntax.
Your conventions should be extended to accommodate the particularities of any
preprocessor in use. The following guidelines are in reference to Sass.

* Limit nesting to 1 level deep. Reassess any nesting more than 2 levels deep.
  This prevents overly specific CSS selectors.
* Avoid large numbers of nested rules. Break them up when readability starts to
  be affected. Preference to avoid nesting that spreads over more than 20
  lines.
* Always place `@extend` statements on the first lines of a declaration
  block.
* Where possible, group `@include` statements at the top of a declaration
  block, after any `@extend` statements.
* Consider prefixing custom functions with `x-` or another namespace. This
  helps to avoid any potential to confuse your function with a native CSS
  function, or to clash with functions from libraries.

```scss
.selector-1 {
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

Utilisez des noms clairs et réfléchis pour les classes HTML. Choisissez un modçle de nommage consistent et compréhensif qui a du sens à la fois dans les fichiers HTML et dans les fichiers CSS.

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

Un exemple de plusieurs conventions.

```css
/* ==========================================================================
   Construction de la grille
   ========================================================================== */

/*
 * Exemple de HTML:
 *
 * <div class="grid">
 *     <div class="cell cell-5"></div>
 *     <div class="cell cell-5"></div>
 * </div>
 */

.grid {
    overflow: visible;
    height: 100%;
    /* Empêche d'entourer les cellules en inline-block */
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

L'organisation du code est une partie importante de n'importe quelle base de code CSS et cruciale pour les grosses bases de code.

* Séparer de manière logique les différentes parties de code.
* Utilisez des fichiers distincts (concatenés au cours de l'étape de compilation) pour aider à séparer le code des différents composants.
* Si vous utilisez un pré-processeur, stockez le code récurrent dans des variables pour la couleur, la typographie, etc.


<a name="compilation-et-deploiement"></a>
## 8. Compilation et déploiement

Les projets devraient toujours essayer de mentionner des façons génériques grâce auxquelles le code source peut être validé, testé, compressé, et versionné en préparation à l'utilisation en production.
 Pour ça, [grunt](https://github.com/cowboy/grunt) de Ben Alman est un excellent outil.


<a name="remerciements"></a>
## Remerciements

Merci à tous ceux qui ont contribué à [idiomatic.js](https://github.com/rwldrn/idiomatic.js). Cela a été une source d'inspiration, de citations et de conventions.
