# Principes d’écriture consistante et idiomatique de CSS

Le document suivant met en place un guide de développement de CSS raisonnable. Il n’est pas destiné à être suivi à la lettre et je ne veux pas imposer mais préférences de style sur le code des autres. Cependant ce guide encourage tout-de-même l’utilisation de conventions existantes, communes et raisonnables.

Ceci est un document vivant et de nouvelles idées sont les bien-venues. Contribuez s’il-vous-plaît.

## Traductions

* [Anglais](https://github.com/necolas/idiomatic-css)
* [Italian](https://github.com/necolas/idiomatic-css/tree/master/translations/it-IT)
* [日本語](https://github.com/necolas/idiomatic-css/tree/master/translations/ja-JP)
* [Português (Brasil)](https://github.com/necolas/idiomatic-css/tree/master/translations/pt-BR)
* [Srpski](https://github.com/necolas/idiomatic-css/tree/master/translations/sr)
* [Türkçe](https://github.com/necolas/idiomatic-css/tree/master/translations/tr-TR)

## Table des matières

1. [Principes généraux](#principes-generaux)
2. [Espacement](#espacement)
3. [Commentaires](#commentaires)
4. [Format](#format)
5. [Appellation](#appellation)
6. [Exemple pratique](#exemple)
7. [Organisation](#organisation)
8. [Création et déploiement](#creation-et-deploiement)

[Remerciements](#remerciements)

<a name=“principes-generaux”></a>
## 1. Principes généraux

> « Une des parties pour être un bon administrateur à un projet est de
> réaliser qu’écrire du code pour vous-même est une mauvaise idée (Bad Idea™).
> Si des milliers de gens utilisent votre code, essayez d’écrire votre
> code avec un maximum de clarté, et non pas par une préférence
> personnelle pour devenir malin dans le “spec.” » - Idan Gazit

* Tout le code dans toute base de code doit avoir l’air d’avoir été écrit
  par une seule et même personne, n’importe le nombre de gens y ayant contribué.
* Adhérez strictement au style choisi.
* Si en doute, utilisez des conventions existantes et/ou communes.

<a name=“espacement”></a>
## 2. Espacement

Il n’y a qu’un style qui doit exister au long du code de votre projet. Soyez toujours
consistent dans votre espacement. Utilisez cet espacement pour améliorer la lecture.

* Ne _jamais_ mélanger des espaces et des tabulations pour le renfoncement.
* Choisissez entre des tabulations douces (espaces) ou des vrais tabulations. Soyez consistent
  sans exception. (Préférence : espaces)
* Si vous utilisez des espaces, choisissez le nombre de caractères de renfoncement par
  niveau. (Préférence : 4 espaces)

Conseil : configurez votre éditeur afin montrer les invisibles (ou « show invisibles »).
Ceci va vous aider à éliminer les espaces de fin de lignes, éliminer les lignes vide
non renfoncées et éviter de polluer les « commits. »

<a name=“commentaires”></a>
## 3. Commentaires

Du code bien commenté est extrêmement important. Prenez du temps pour décrire les
composants, comment ils fonctionnent, leurs limitations et leur construction. Ne
laissez pas les autres dans l’équipe deviner l’utilité de code obscure ou singulier.

Le style des commentaires doit être simple et consistant dans une base de code.

* Placez les commentaires sur une nouvelle ligne au-dessus de leur sujet.
* Évitez les commentaires de fin de ligne.
* Garder la longueur des lignes sous un maximum raisonnable, ex. 80 colonnes.
* Utilisez les commentaires de façon libérale pour diviser le code CSS en sections discrètes.
* Utilisez des commentaires de « cas de phrases » et un renfoncement de texte consistent.

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
 * Bloc de commentaire groupé
 * Idéal pour les explications sur plusieurs lignes
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
// Bloc de commentaire groupé
// Idéal pour les explications sur plusieurs lignes
//

// Commentaire de base
```


<a name="format"></a>
## 4. Format

Le format de code choisi doit assurer qu’il soit : facile à lire ; facile
à commenter ; que les chances  d’introduction accidentelle d’erreurs soit
minimisées ; et qu’il entraîne des différences et des blâmes utiles.

1. Un sélecteur discret par ligne dans des conditions de sélecteurs multiples.
2. Un seul espace avant la parenthèse « { » d’une condition.
3. Une déclaration par ligne dans un bloc de déclarations.
4. Un niveau de renfoncement par déclaration.
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
Ma préférence est de garder les propriétés proches ensemble et pour les
propriétés de structure importantes (c-à-d position et boîte-modèle) d’être
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

#### Exceptions et déviations

