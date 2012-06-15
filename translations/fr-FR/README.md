# Principes d’écriture de CSS consistante et idiomatique

Le document suivant met en place un guide de développement de CSS raisonnable. Il n’est pas destiné à être suivi à la lettre et je ne veux pas imposer mais préférences de style sur le code des autres. Cependant ce guide encourage tout-de-même l’utilisation de conventions existantes, communes et raisonnables.

Ceci est un document vivant et de nouvelles idées sont les bien-venues. Contribuez s’il-vous-plaît.

* [Idiomatic CSS in English (Original)](https://github.com/necolas/idiomatic-css)

## Table des matières

1. [Principes généraux](#principes-generaux)
2. [Espacement et retraits](#espacement)
3. [Commentaires](#commentaires)
4. [Formatage](#formatage)
5. [Noms](#noms)
6. [Exemple pratique](#exemple)
7. [Organisation](#organisation)
8. [Création et déploiement](#creation-et-deploiement)

[Remerciements](#remerciements)

<a name="principes-generaux"></a>
## 1. Principes généraux

> « Pour être un bon administrateur à un projet, un des atouts est de
> réaliser qu’écrire du code pour vous-même est une mauvaise idée (Bad Idea™).
> Si des milliers de gens utilisent votre code, essayez d’écrire votre
> code avec un maximum de clarté, et non pas par une préférence
> personnelle pour devenir malin dans le “spec.” » - Idan Gazit

* Le code d'un projet doit avoir l’air d’avoir été écrit
  par une seule et même personne, quel que soit le nombre de gens y ayant contribué.
* Adhérez strictement au style choisi.
* Dans le doute, utilisez des conventions existantes et/ou communes.

<a name="espacement"></a>
## 2. Espacement et retrait

Il n’y a qu’un style qui doit exister au long du code de votre projet. Soyez toujours
consistent dans votre façon d'indenter. Utilisez cet espacement pour améliorer la lecture.

* Ne _jamais_ mélanger des espaces et des tabulations pour l'indentation.
* Choisissez entre des tabulations douces (espaces) ou des vrais tabulations. Soyez consistent
  sans exception. (Préférence : espaces)
* Si vous utilisez des espaces, choisissez le nombre de caractères de retrait par
  niveau. (Préférence : 4 espaces)

Conseil : configurez votre éditeur afin montrer les invisibles (ou « show invisibles »).
Ceci va vous aider à éliminer les espaces de fin de lignes, éliminer les lignes vide
non renfoncées et éviter de polluer les « commits. »

<a name="commentaires"></a>
## 3. Commentaires

Du code bien commenté est extrêmement important. Prenez du temps pour décrire les
composants, comment ils fonctionnent, leurs limitations et leur construction. Ne
laissez pas les autres dans l’équipe deviner l’utilité de code obscure ou singulier.

Le style des commentaires doit être simple et consistant dans une base de code.

* Placez les commentaires sur une nouvelle ligne au-dessus de leur sujet.
* Évitez les commentaires de fin de ligne.
* Garder la longueur des lignes sous un maximum raisonnable, ex. 80 colonnes.
* Utilisez les commentaires de façon libérale pour diviser le code CSS en sections discrètes.
* Utilisez des commentaires de « cas de phrases » et une indentation consistante.

Conseil : configurez votre éditeur afin de créer des raccourcis pour produire le style
de commentaire décidé.

#### Exemple CSS :

```css
/* ==========================================================================
   Bloc de commentaire de section
   ========================================================================== */

/* Bloc de commentaire de sous-section
   ========================================================================== */

/*
 * Bloc de commentaire groupe
 * Ideal pour les explications sur plusieurs lignes
 */

/* Commentaire de base */
```

#### Exemple SCSS :

```scss
// ==========================================================================
// Bloc de commentaire de section
// ==========================================================================

// Bloc de commentaire de sous-section
// ==========================================================================

//
// Bloc de commentaire groupe
// Ideal pour les explications sur plusieurs lignes
//

// Commentaire de base
```


<a name="formatage"></a>
## 4. Formatage

Le formatage de code choisi doit assurer qu’il soit : facile à lire ; facile
à commenter ; que les chances  d’introduction accidentelle d’erreurs soit
minimisées ; et qu’il entraîne des différences et des blâmes utiles.

1. Un sélecteur discret par ligne dans des conditions de sélecteurs multiples.
2. Un seul espace avant la parenthèse « { » d’une condition.
3. Une déclaration par ligne dans un bloc de déclarations.
4. Un niveau de retrait par déclaration.
5. Un seul espace après les deux-points d’une déclaration.
6. Ajoutez toujours un point-virgule à la fin de la dernière déclaration d’un bloc.
7. Placez la parenthèse « } » dans la même colonne que le premier caractère
   de la condition.
8. Séparez chaque condition par une ligne vide.

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

#### Ordre de déclaration

Les déclarations doivent toujours être ordonnées selon un seul principe.
Je préfère garder les propriétés proches ensemble et pour les
propriétés de structure importantes (c-à-d position et « box-model ») d’être
déclarées avant la typographie, l’arrière-plan et es propriétés de couleur.

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

L’ordre alphabétique est aussi populaire, mais le problème est qu’il sépare
les propriétés apparentées. Par exemple, les décalages de position ne sont
plus regroupées et les propriétés de boîte-modèle peuvent se trouver répandues
au travers du bloc de déclaration.

#### Exceptions et légères déviations

De longs blocs de déclarations d’une ligne peuvent utiliser un style unilinéaire,
légèrement différent. Dans ce cas un espace doit être inclus après la parenthèse
d’ouverture et avant la parenthèse de fermeture.

```css
.selecteur-1 { width: 10%; }
.selecteur-2 { width: 20%; }
.selecteur-3 { width: 30%; }
```

Les longues valeurs de propriétés séparées par des virgules – tels que les gradients
ou les ombres – peuvent être arrangées sur plusieurs lignes dans un effort visant à
améliorer la lecture et les différences. Il y a plusieurs formats qui peuvent être
utilisés ; un exemple est montré en-dessous.

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

* Utilisez des valeurs hexadécimales en minuscules, ex. `aaa`.
* Utilisez des guillemets simples (‘) ou doubles (“) avec consistance. Je préfère
  les doubles guillemets, ex. `content: “”`.
* Utilisez toujours des guillemets dans les valeurs des attributs,
  ex. `input[type=“checkout”]`.
* _Lorsque valable_, évitez des unités pour des valeurs nulles, ex. `margin: 0`.

### Préprocesseurs : considérations additionnelles de formatage

Les différents pré-processeurs CSS existant offrent des fonctionnalités et des syntaxes
différentes. Vos conventions doivent être adaptées pour convenir aux particularités
de tout préprocesseur en utilisation.

* Limitez le niveau de retrait à 1. Réévaluer toute imbrication à plus de 2
  niveaux de profondeur. Ceci prévient l’utilisation de sélecteurs CSS trop spécifiques.
* Évitez de grands nombres de règles imbriquées. Divisez les quand la lecture est
  affectée. Préférence d’éviter toute imbrication de plus de 20 lignes.
* Placez toujours des déclarations `@extend` sur la première ligne d’un bloc de
  déclarations.
* Lorsque possible, groupez les déclarations `@include` en haut des blocs de
  déclaration, au-dessous de toute déclaration `@extend`.
* Considérez préfixer les fonctions personnelles avec `x-` ou un autre préfix, afin
  d’éviter toute confusion potentielle entre votre fonction et une fonction CSS native,
  ou toute confrontation avec des fonctions de bibliothèques de code.

```scss
.selecteur-1 {
    @extend .autre-regles;
    @include clearfix();
    @include box-sizing(border-box);
    width: x-grid-unit(1);
    // autres declarations
}
```

<a name="noms"></a>
## 5. Noms

Vous n’êtes pas un compilateur/compresseur de code humain et n’essayez pas d’en être un.

Utilisez des noms claires et sensés pour les classes HTML. Choisissez une convention
consistante et compréhensible de chois des noms qui est logique dans le code HTML et le
code CSS.

```css
/* Exemple de code mal nomme */

.def {
    overflow: auto;
}

.cc {
    background: #000;
}

/* Exemple de code mieux nomme */

.defile {
    overflow: auto;
}

.colonne-corps {
    background: #000;
}
```

<a name="exemple"></a>
## 6. Exemple Pratique

Un exemple de plusieurs conventions.

```css
/* ==========================================================================
   Presentation en grille
   ========================================================================== */

/*
 * Exemple HTML:
 *
 * <div class=“grille”>
 *     <div class="cellule cellule-5”></div>
 *     <div class="cellule cellule-5”></div>
 * </div>
 */

.grille {
    overflow: visible;
    height: 100%;
    /* Previent les cellules inline-block de creer une nouvelle ligne */
    white-space: nowrap;
    /* Retire l’espace intercellulaire */
    font-size: 0;
}

.cellule {
    box-sizing: border-box;
    position: relative;
    overflow: hidden;
    width: 20%;
    height: 100%;
    /* Cree l’espace intercellulaire */
    padding: 0 10px;
    border: 2px solid #333;
    vertical-align: top;
    /* Remet l’espace blanc */
    white-space: normal;
    /* Remet la taille de la police */
    font-size: 16px;
}

/* Etats des cellules */

.cellule.est-animee {
    background-color: #fffdec;
}

/* Dimensions des cellules
   ========================================================================== */

.cellule-1 { width: 10%; }
.cellule-2 { width: 20%; }
.cellule-3 { width: 30%; }
.cellule-4 { width: 40%; }
.cellule-5 { width: 50%; }

/* Modificateurs des cellules
   ========================================================================== */

.cellule--detail,
.cellule--important {
    border-width: 4px;
}
```

<a name="organisation"></a>
## 7. Organisation

L’organisation du code est aussi important que tout autre élément dans un projet
CSS, et est cruciale pour les gros projets.

* Séparez logiquement les parties distinctes du code.
* Utilisez des fichiers séparés (enchainez les) pour aider à séparer le code en
  composantes distinctes.
* Si vous utilisez un préprocesseur, abstraites le code commun en des variables
  pour la couleur, la typographie,...

<a name=“creation-et-deploiement”></a>
## 8. Création et déploiement

Un projet doit toujours essayer d’inclure une convention générique par laquelle
le code peut être implémenté avec JSLint, testé, compressé et versionné en
préparation à la production. Pour cette tâche, [grunt](https://github.com/cowboy/grunt)
par Ben Alman est une utilité excellente.

<a name="remerciements"></a>
## Remerciements

Merci à tous qui ont contribué à [idiomatic.js](https://github.com/rwldrn/idiomatic.js).
C’était une source d’inspiration, de dictons et de guides.