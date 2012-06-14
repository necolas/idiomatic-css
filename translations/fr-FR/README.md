# Principes d’écriture consistante, idiomatic CSS

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
3. [Notes](#notes)
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

* Ne _jamais_ mélanger des espaces et des « tabs » pour le renfoncement.
* Choisissez entre des « soft tabs » (espaces) ou des vrais « tabs. » Soyez consistent
  sans exception. (Préférence : espaces)
* Si vous utilisez des espaces, choisissez le nombre de caractères de renfoncement par
  niveau. (Préférence : 4 espaces)

Conseil : configurer votre éditeur pour montrer les invisibles (ou « show invisibles »).
Ceci va vous aider à éliminer les espaces de fin de lignes, éliminer les lignes vide
non renfoncées et éviter de polluer les « commits. »

<a name=“notes”></a>
## 3. Notes