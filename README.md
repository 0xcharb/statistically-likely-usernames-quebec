# statistically-likely-usernames-quebec
Listes de noms d’utilisateur statistiquement classées pour le Québec, destinées aux tests de sécurité autorisés et à la recherche.

# Statistically Likely Usernames - Québec

> Français d'abord · [English below](#english)

Ce dépôt vise une **couverture québécoise historiquement plausible**, plutôt qu'un produit cartésien de tous les prénoms modernes avec tous les noms de famille modernes.

> **Version publique : v0.1.**  
> `alexandre` est volontairement placé au rang #1 pour rester cohérent avec les noms de fichiers.

## Français

### Principe

- **Prénoms :** uniquement des prénoms ayant atteint le **Top 50** au Québec dans au moins une des années de référence **1980, 1985, 1990 ou 1995**, garçons et filles.
- **Noms de famille :** uniquement les noms du **Top 50 québécois de 1881** publié par l'ISQ.

Les prénoms présents dans plusieurs années historiques sont classés plus haut.

### Prénoms secondaires et composés

Les prénoms secondaires séparés par un espace ne sont pas concaténés :

```text
Jean François -> jean
Marie Eve     -> marie
Marc Antoine  -> marc
```

Un vrai prénom composé qui existe avec un trait d'union peut être conservé si **toutes ses composantes** appartiennent elles-mêmes au corpus historique :

```text
Jean-Christophe -> jean-christophe
Marie-Eve       -> marie-eve
```

Cela permet d'écarter automatiquement des formes qui ne correspondent pas au profil historique retenu sans essayer de deviner l'origine d'une personne.

### Taille du corpus

- **268 prénoms** historiques (simples + composés valides)
- **49 noms de famille** historiquement établis
- **13,132 couples prénom/nom** par format complet

Le projet privilégie volontairement la **qualité des combinaisons** plutôt que de forcer artificiellement 1 000 000 entrées.

### Fichiers

| Fichier | Entrées |
|---|---:|
| `alexandre.txt` | 268 |
| `tremblay.txt` | 49 |
| `alexandre.tremblay.txt` | 13,132 |
| `alexandretremblay.txt` | 13,132 |
| `atremblay.txt` | 1,127 |
| `alexandret.txt` | 3,752 |
| `jjs.txt` | 17,576 |
| `awesome-mix-vol1.txt` | 25,800 |
| `awesome-mix-vol2.txt` | 49,400 |
| `top-formats.txt` | 122,096 |

### Classement

Pour les prénoms, un score historique est calculé à partir de leur position dans les quatre snapshots :

```text
points = 51 - rang
score = somme(points sur 1980, 1985, 1990, 1995)
```

Pour les couples :

```text
score_rang = rang_prenom × rang_nom
```

`alexandre` est ensuite épinglé au rang #1 par convention de nommage du dépôt.

### Sources

Les données modernes officielles de Retraite Québec couvrent les garçons et les filles depuis 1980. Cette version utilise volontairement des snapshots historiques pour limiter le corpus aux prénoms durablement établis au Québec.

Les noms de famille sont filtrés avec la table ISQ des 50 premiers noms de famille en 1881.

Voir [`SOURCES.md`](SOURCES.md).

### Utilisation responsable

Pour tests de sécurité autorisés, recherche, laboratoires et CTF uniquement.

---

<a id="english"></a>

# English

This repository prioritizes **historically plausible Québec username combinations** instead of blindly crossing every modern first name with every modern surname.

> **Public version: v0.1.**  
> `alexandre` is intentionally pinned to rank #1 for filename consistency.

### Historical filter

- **First names:** only names that reached the Québec **Top 50** in at least one reference year: **1980, 1985, 1990, 1995**, across boys and girls.
- **Surnames:** only surnames appearing in the ISQ **Top 50 Québec surnames in 1881**.

Space-separated secondary given names are reduced to the primary given name. Explicit hyphenated compounds are retained only when every component is itself part of the historical first-name core.

### Corpus size

- **268 historical first names**
- **49 historical surnames**
- **13,132 first-name/surname pairs per full-name format**

The project intentionally favors plausibility over artificial list size.

See [`SOURCES.md`](SOURCES.md).
