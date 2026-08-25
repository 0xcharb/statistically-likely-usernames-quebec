# statistically-likely-usernames-quebec
Listes de noms d’utilisateur statistiquement classées pour le Québec, destinées aux tests de sécurité autorisés et à la recherche.

# Statistically Likely Usernames - Québec

> Français d'abord · [English below](#english)

Listes de noms d'utilisateur statistiquement plausibles adaptées au Québec, inspirées du projet [InsideTrust/statistically-likely-usernames](https://github.com/insidetrust/statistically-likely-usernames).

Ce dépôt est conçu pour les **tests de sécurité autorisés**, les laboratoires, les CTF, la recherche et la validation de conventions de noms d'utilisateur. Il ne contient pas de comptes réels : les entrées sont **générées à partir de listes agrégées de prénoms masculins et féminins et de noms de famille**.

> **Version actuelle : v0.1 - prototype mixte.**  
> Les listes sont ordonnées selon un modèle de rang transparent. `alexandre` est volontairement épinglé au rang #1 pour garder les listes cohérentes avec les noms de fichiers. Les autres entrées suivent le classement mixte du projet.

---

## Français

### Pourquoi ce projet?

Le projet original d'InsideTrust vise à produire des listes où les formats et les noms les plus plausibles apparaissent tôt, par exemple :

```text
jsmith
john.smith
smithj
```

Cette version applique la même idée au Québec, avec des conventions adaptées aux noms francophones et aux noms composés :

```text
atremblay
alexandre.tremblay
tremblay.alexandre
marie-eve.tremblay
metremblay
```

Les accents sont retirés, mais les **traits d'union faisant réellement partie d'un prénom ou d'un nom sont conservés**.

Exemples :

```text
François        -> francois
Côté            -> cote
Lévesque        -> levesque
Jean-Christophe -> jean-christophe
St-Pierre       -> st-pierre
D'Amours        -> damours
```

---

## Commencer ici

Si le format de nom d'utilisateur de la cible autorisée est inconnu, commencer par :

| Fichier | Entrées | Utilité |
|---|---:|---|
| `awesome-mix-vol1.txt` | 25 800 | Premier passage compact, plusieurs formats intercalés |
| `awesome-mix-vol2.txt` | 49 400 | Suite de Vol. 1, sans doublon avec Vol. 1 |
| `top-formats.txt` | 1 000 000 | Mélange large de formats, intercalé et dédupliqué |

---

## Fichiers disponibles

Le nom des fichiers sert d'exemple du format. **Alexandre Tremblay** est utilisé comme nom représentatif du projet. `alexandre` est volontairement placé en première position de la liste de prénoms pour que les noms de fichiers et les premières entrées restent cohérents.

Cela **ne signifie pas** qu'« Alexandre Tremblay » est prouvé comme étant le nom complet réel le plus fréquent au Québec.

### Listes de base

| Fichier | Entrées | Contenu |
|---|---:|---|
| `alexandre.txt` | 10 000 | Prénoms et masculins féminins classés |
| `tremblay.txt` | 250 | Noms de famille québécois classés |

### Prénom + nom

| Fichier | Format | Entrées |
|---|---|---:|
| `alexandre.tremblay.txt` | `{prenom}.{nom}` | 250 000 |
| `tremblay.alexandre.txt` | `{nom}.{prenom}` | 250 000 |
| `alexandretremblay.txt` | `{prenom}{nom}` | 250 000 |
| `tremblayalexandre.txt` | `{nom}{prenom}` | 250 000 |
| `alexandre_tremblay.txt` | `{prenom}_{nom}` | 250 000 |
| `tremblay_alexandre.txt` | `{nom}_{prenom}` | 250 000 |

### Initiale du prénom + nom

| Fichier | Format | Entrées |
|---|---|---:|
| `atremblay.txt` | `{initiale_prenom}{nom}` | 6 500 |
| `tremblaya.txt` | `{nom}{initiale_prenom}` | 6 500 |
| `a.tremblay.txt` | `{initiale_prenom}.{nom}` | 6 500 |
| `tremblay.a.txt` | `{nom}.{initiale_prenom}` | 6 500 |
| `a_tremblay.txt` | `{initiale_prenom}_{nom}` | 6 500 |
| `tremblay_a.txt` | `{nom}_{initiale_prenom}` | 6 500 |

L'ordre n'est pas alphabétique. Les prénoms partageant la même initiale sont regroupés pour estimer le poids de cette initiale, puis combinés avec le rang du nom de famille.

### Prénom + initiale du nom

| Fichier | Format | Entrées |
|---|---|---:|
| `alexandret.txt` | `{prenom}{initiale_nom}` | 50 000 |
| `talexandre.txt` | `{initiale_nom}{prenom}` | 50 000 |
| `alexandre.t.txt` | `{prenom}.{initiale_nom}` | 50 000 |
| `t.alexandre.txt` | `{initiale_nom}.{prenom}` | 50 000 |

### Initiales de prénoms composés

La version mixte utilise **Marie-Eve** comme exemple de prénom composé, donc les fichiers utilisent `me`.

| Fichier | Format | Entrées |
|---|---|---:|
| `metremblay.txt` | `{initiales_prenom_compose}{nom}` | 44,000 |
| `tremblayme.txt` | `{nom}{initiales_prenom_compose}` | 44,000 |
| `me.tremblay.txt` | `{initiales}.{nom}` | 44,000 |
| `tremblay.me.txt` | `{nom}.{initiales}` | 44,000 |
| `me_tremblay.txt` | `{initiales}_{nom}` | 44,000 |
| `tremblay_me.txt` | `{nom}_{initiales}` | 44,000 |

Ces fichiers sont générés **uniquement à partir de vrais prénoms composés présents dans la liste de base**.

### Autres listes

| Fichier | Entrées | Notes |
|---|---:|---|
| `atremblay2.txt` | 5 000 | Suffixe de collision `2` |
| `tremblaya2.txt` | 5 000 | Format inversé avec suffixe `2` |
| `jjs.txt` | 17 576 | Toutes les combinaisons ASCII de trois lettres; classement heuristique |
| `awesome-mix-vol1.txt` | 25 800 | Mélange intercalé |
| `awesome-mix-vol2.txt` | 49 400 | Continuation sans chevauchement |
| `top-formats.txt` | 1 000 000 | Mélange large, intercalé et dédupliqué |

---

## Méthode de classement

La v0.1 utilise un score de rang ordinal :

```text
score_rang = rang_prenom × rang_nom
```

Plus le score est petit, plus la combinaison apparaît tôt.

Pour certaines transformations comme les initiales, une forme équivalente est utilisée :

```text
poids = 1 / rang
```

Les poids des prénoms qui produisent la même initiale sont additionnés avant la combinaison avec les noms de famille.

**Exception volontaire : `alexandre` est toujours placé au rang #1** pour conserver une cohérence entre le nom des fichiers et leur contenu. Cette décision est une convention du projet, pas une affirmation statistique.

---

## Sources de données

### Prénoms

La liste actuelle est **mixte**.

- La base masculine provient du classement Retraite Québec utilisé dans les versions précédentes.
- La couche féminine utilise des données québécoises publiées sur les prénoms féminins fréquents et est fusionnée avec la base masculine.

La version v1.0 devrait idéalement être reconstruite directement à partir des deux jeux officiels complets Retraite Québec, garçons et filles.

### Noms de famille

Les noms de famille proviennent du travail de l'**Institut de la statistique du Québec (ISQ)** sur les noms de famille au Québec :

https://statistique.quebec.ca/fr/document/noms-de-famille-au-quebec

**Limitation actuelle :** seulement **250 noms de famille vérifiés et classés** sont utilisés. L'ISQ publie une ressource couvrant les 5 000 principaux noms.

Voir [`SOURCES.md`](SOURCES.md) pour les détails et les limites de provenance.

---

## Normalisation

Toutes les listes distribuées suivent ces règles :

- minuscules;
- ASCII seulement;
- accents retirés;
- apostrophes retirées;
- espaces retirés;
- traits d'union structurels conservés;
- aucun trait d'union artificiel ajouté entre prénom et nom;
- doublons retirés à l'intérieur de chaque fichier.

Exemple :

```text
Jean-François Côté
-> jean-francois.cote
-> cote.jean-francois
-> jean-francoiscote
```

et non :

```text
jeanfrancois.cote
jean-françois.côté
```

---

## Limites connues

v0.1 est volontairement un prototype.

1. Seulement 250 noms de famille sont utilisés.
2. La couverture des prénoms est mixte, mais la liste des prénoms féminins reste incomplète.
3. `alexandre` est volontairement épinglé au rang #1 pour la cohérence des fichiers.
4. Le score de rang n'est pas une probabilité réelle.
5. `jjs.txt` reste un classement heuristique.
6. Le modèle suppose qu'un prénom et un nom de famille peuvent être combinés indépendamment pour les besoins du classement.
7. Les listes ne prouvent pas qu'un nom complet donné correspond à une personne réelle.

---

## Utilisation responsable

Ces listes sont destinées aux **tests autorisés**, à la recherche et aux environnements de laboratoire.

N'utilisez pas ce projet pour accéder à des comptes, systèmes ou services sans autorisation.

---

## Inspiration

Ce projet est inspiré de :

**InsideTrust - statistically-likely-usernames**  
https://github.com/insidetrust/statistically-likely-usernames

---

<a id="english"></a>

# English

Statistically plausible username wordlists adapted to Québec, inspired by [InsideTrust/statistically-likely-usernames](https://github.com/insidetrust/statistically-likely-usernames).

This repository is intended for **authorized security testing**, labs, CTFs, research, and username-convention validation. It does not contain known real accounts: entries are **generated from aggregate female and male first-name data and surname lists**.

> **Current version: v0.1 - mixed prototype.**  
> Lists use a transparent rank-based model. `alexandre` is intentionally pinned to rank #1 so the data remains consistent with the filenames.

---

## Why this project?

The original InsideTrust project aims to put statistically useful username guesses early in a list, for example:

```text
jsmith
john.smith
smithj
```

This Québec version applies the same idea to local naming patterns and compound French names:

```text
atremblay
alexandre.tremblay
tremblay.alexandre
marie-eve.tremblay
metremblay
```

Accents are removed, while **hyphens that are actually part of a name are preserved**.

---

## Start here

| File | Entries | Purpose |
|---|---:|---|
| `awesome-mix-vol1.txt` | 25,800 | Compact first pass across several interleaved formats |
| `awesome-mix-vol2.txt` | 49,400 | Continuation of Vol. 1 with no overlap |
| `top-formats.txt` | 1,000,000 | Broad interleaved and deduplicated format mix |

---

## Available files

Filenames demonstrate their format. **Alexandre Tremblay** is the representative name used by the project, and `alexandre` is intentionally kept as the first first-name entry for consistency.

This **does not mean** that Alexandre Tremblay has been proven to be the most common real full name in Québec.

### Base lists

| File | Entries | Contents |
|---|---:|---|
| `alexandre.txt` | 10,000 | Ranked mixed male and female first names |
| `tremblay.txt` | 250 | Ranked Québec surnames |

### First name + surname

| File | Format | Entries |
|---|---|---:|
| `alexandre.tremblay.txt` | `{firstname}.{surname}` | 250,000 |
| `tremblay.alexandre.txt` | `{surname}.{firstname}` | 250,000 |
| `alexandretremblay.txt` | `{firstname}{surname}` | 250,000 |
| `tremblayalexandre.txt` | `{surname}{firstname}` | 250,000 |
| `alexandre_tremblay.txt` | `{firstname}_{surname}` | 250,000 |
| `tremblay_alexandre.txt` | `{surname}_{firstname}` | 250,000 |

### First initial + surname

| File | Format | Entries |
|---|---|---:|
| `atremblay.txt` | `{first_initial}{surname}` | 6,500 |
| `tremblaya.txt` | `{surname}{first_initial}` | 6,500 |
| `a.tremblay.txt` | `{first_initial}.{surname}` | 6,500 |
| `tremblay.a.txt` | `{surname}.{first_initial}` | 6,500 |
| `a_tremblay.txt` | `{first_initial}_{surname}` | 6,500 |
| `tremblay_a.txt` | `{surname}_{first_initial}` | 6,500 |

The list is not alphabetical. First names sharing an initial are aggregated before being combined with surname rank.

### First name + surname initial

| File | Format | Entries |
|---|---|---:|
| `alexandret.txt` | `{firstname}{surname_initial}` | 50,000 |
| `talexandre.txt` | `{surname_initial}{firstname}` | 50,000 |
| `alexandre.t.txt` | `{firstname}.{surname_initial}` | 50,000 |
| `t.alexandre.txt` | `{surname_initial}.{firstname}` | 50,000 |

### Compound first-name initials

The mixed prototype uses **Marie-Eve** as its compound-name example, therefore these filenames use `me`.

| File | Format | Entries |
|---|---|---:|
| `metremblay.txt` | `{compound_first_initials}{surname}` | 44,000 |
| `tremblayme.txt` | `{surname}{compound_first_initials}` | 44,000 |
| `me.tremblay.txt` | `{initials}.{surname}` | 44,000 |
| `tremblay.me.txt` | `{surname}.{initials}` | 44,000 |
| `me_tremblay.txt` | `{initials}_{surname}` | 44,000 |
| `tremblay_me.txt` | `{surname}_{initials}` | 44,000 |

### Other lists

| File | Entries | Notes |
|---|---:|---|
| `atremblay2.txt` | 5,000 | Collision suffix `2` |
| `tremblaya2.txt` | 5,000 | Reversed collision format |
| `jjs.txt` | 17,576 | Every three-letter ASCII combination; heuristic ordering |
| `awesome-mix-vol1.txt` | 25,800 | Interleaved mix |
| `awesome-mix-vol2.txt` | 49,400 | Non-overlapping continuation |
| `top-formats.txt` | 1,000,000 | Broad interleaved and deduplicated mix |

---

## Ranking method

v0.1 uses an ordinal rank score:

```text
rank_score = first_name_rank × surname_rank
```

For collapsed transformations such as initials, rank-derived weights are aggregated.

**Intentional exception: `alexandre` is always pinned to rank #1** to keep the filenames and the contents consistent. This is a project convention, not a statistical claim.

---

## Data sources

### First names

The current first-name list is **mixed**.

- The male base comes from the Retraite Québec-derived ranking used in earlier versions.
- A Québec female-name layer is merged into that base.
- Female long-tail coverage is not yet as complete as the male side in this prototype.

A future v1.0 should ideally rebuild directly from both complete official Retraite Québec boys and girls datasets.

### Surnames

Surnames are based on the **Institut de la statistique du Québec (ISQ)** work on Québec family names:

https://statistique.quebec.ca/fr/document/noms-de-famille-au-quebec

**Current limitation:** only **250 verified ranked surnames** are included.

See [`SOURCES.md`](SOURCES.md) for provenance and limitations.

---

## Normalization

- lowercase;
- ASCII only;
- accents removed;
- apostrophes removed;
- spaces removed;
- structural hyphens preserved;
- no artificial first/last hyphen separator;
- duplicates removed within each file.

---

## Known limitations

1. Only 250 surnames are included.
2. The corpus is mixed, but female long-tail coverage remains incomplete.
3. `alexandre` is intentionally pinned to rank #1 for repository consistency.
4. Rank score is not a true probability.
5. `jjs.txt` remains heuristic.
6. First names and surnames are treated as independently combinable for ranking.
7. Generated full names do not prove that a corresponding real person exists.

---

## Responsible use

These lists are intended for **authorized testing**, research, and lab environments.

Do not use this project to access accounts, systems, or services without permission.

---

## Inspiration

This project is inspired by:

**InsideTrust - statistically-likely-usernames**  
https://github.com/insidetrust/statistically-likely-usernames
