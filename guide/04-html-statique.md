# 04 — HTML statique du frontend

## Objectif

Cette étape sert à créer les premières pages publiques du projet en HTML statique.

On ne travaille pas encore :

```txt
CSS
PHP
base de données
boucles
administration
JavaScript
```

On construit d’abord la structure des pages.

Le HTML doit pouvoir être lu et compris avant toute mise en forme.

À cette étape, le navigateur affiche les pages avec son style par défaut. C’est volontaire. Avant d’écrire du CSS, il faut observer ce que le HTML fait déjà naturellement.

---

## Règles de l’étape

Pendant toute cette étape :

```txt
aucun fichier CSS
aucune balise <style>
aucun attribut style=""
aucune classe CSS décorative
aucun display flex
aucun grid
aucun positionnement visuel
aucun JavaScript
aucun PHP dynamique
aucune requête SQL
```

Règle stricte :

```txt
Aucun <div>.
```

Les `<div>` sont interdits à cette étape.

Si vous pensez avoir besoin d’un `<div>`, c’est probablement que vous n’avez pas encore identifié la bonne balise HTML.

Balises à privilégier :

```txt
header
nav
main
section
article
aside
footer
h1 à h6
p
ul / ol / li
dl / dt / dd
figure / figcaption
form
fieldset / legend
label
input
textarea
button
address
```

`<span>` est toléré uniquement s’il y a une justification claire : isoler une petite portion de texte sans signification structurelle propre.

Exemple acceptable :

```html
<p>Statut : <span>Publié</span></p>
```

Mais si le contenu a une vraie signification, utilisez une balise plus précise.

---

# 1. Créer `item-show.html`

## Objectif

La première page à créer est la page détail d’un item.

Fichier :

```txt
item-show.html
```

Cette page est prioritaire parce qu’elle oblige à réfléchir à tout ce qu’un item peut contenir.

Elle prépare :

```txt
la future table item
la catégorie
le thème
les tags
l’image principale
le contenu complet
les métadonnées
la future view views/item/show.php
la future route /item/show/3
```

On commence par une page détail parce qu’un seul item permet de poser calmement toute la structure.

On ne crée pas encore les items liés.

Les items liés demanderont plus tard des composants de liste ou de carte. Ces composants seront préparés avec le catalogue et la page d’accueil.

---

## Contenu attendu

La page détail doit contenir au minimum :

```txt
nom du site
navigation principale
titre de l’item
image principale
description courte
contenu détaillé
catégorie
thème
tags
métadonnées utiles
lien retour vers le catalogue
footer
```

Cette page doit utiliser toutes les informations principales du projet.

Même si les données sont fictives, elles doivent ressembler aux futures données réelles.

---

## Exemple de structure complète

Cet exemple sert à montrer une approche sémantique pure.

Il ne doit pas être recopié sans adaptation.

Il montre surtout comment organiser la page sans `<div>`.

```html
<!doctype html>
<html lang="fr">
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Nom de l’item — Nom du site</title>
</head>
<body>
    <header>
        <p>Nom du site</p>

        <nav aria-label="Navigation principale">
            <ul>
                <li><a href="home.html">Accueil</a></li>
                <li><a href="item-index.html">Catalogue</a></li>
                <li><a href="item-search.html">Recherche</a></li>
                <li><a href="about.html">À propos</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <article>
            <header>
                <p><a href="item-index.html">Retour au catalogue</a></p>

                <h1>Nom de l’item</h1>

                <p>
                    Description courte de l’item. Cette phrase doit permettre de comprendre
                    rapidement ce que représente le contenu.
                </p>

                <figure>
                    <img src="assets/img/item-placeholder.jpg" alt="Description précise de l’image principale">
                    <figcaption>Image principale associée à l’item.</figcaption>
                </figure>
            </header>

            <section aria-labelledby="description-title">
                <h2 id="description-title">Description</h2>

                <p>
                    Contenu détaillé de l’item. Ce texte peut présenter l’histoire,
                    le contexte, les caractéristiques ou les informations principales.
                </p>

                <p>
                    Un second paragraphe permet de vérifier que la page supporte un contenu
                    plus long et reste lisible sans CSS.
                </p>
            </section>

            <section aria-labelledby="classification-title">
                <h2 id="classification-title">Classification</h2>

                <dl>
                    <dt>Catégorie</dt>
                    <dd>Nom de la catégorie</dd>

                    <dt>Thème</dt>
                    <dd>Nom du thème</dd>

                    <dt>Tags</dt>
                    <dd>tag principal, tag secondaire, tag complémentaire</dd>
                </dl>
            </section>

            <section aria-labelledby="metadata-title">
                <h2 id="metadata-title">Informations</h2>

                <dl>
                    <dt>Statut</dt>
                    <dd>Publié</dd>

                    <dt>Date de publication</dt>
                    <dd>2026-07-03</dd>

                    <dt>Référence</dt>
                    <dd>item-001</dd>
                </dl>
            </section>

            <nav aria-label="Navigation de l’item">
                <ul>
                    <li><a href="item-index.html">Retour au catalogue</a></li>
                    <li><a href="item-search.html">Rechercher un autre item</a></li>
                </ul>
            </nav>
        </article>
    </main>

    <footer>
        <p>Nom du site — Projet ATE</p>
    </footer>
</body>
</html>
```

---

## Observation avant de continuer

Ouvrez la page dans le navigateur.

Sans CSS, vous devez déjà voir :

```txt
le titre principal
les sections
les paragraphes
les listes
les définitions
les liens
l’image
le formulaire de navigation naturel de la page
```

La page sera verticale.

C’est normal.

N’ajoutez pas de CSS pour “faire une colonne”.

Les éléments comme `main`, `article`, `section`, `p`, `dl`, `ul` se placent déjà verticalement parce que ce sont des éléments de bloc.

Mauvais réflexe à éviter plus tard :

```css
main {
    display: flex;
    flex-direction: column;
}
```

Avant d’écrire ce type de CSS, il faut se demander :

```txt
Est-ce que le HTML ne le faisait pas déjà naturellement ?
```

---

## Commit attendu

Quand `item-show.html` est terminé :

```txt
git add item-show.html
git commit -m "Add static item detail page"
```

---

# 2. Créer `item-index.html`

## Objectif

La deuxième page est le catalogue.

Fichier :

```txt
item-index.html
```

Cette page liste plusieurs items.

Elle prépare :

```txt
la future route /item
la future view views/item/index.php
la future boucle PHP
la pagination
le futur composant card
```

Ici, on ne réécrit pas tout le squelette HTML.

Vous reprenez le même squelette général que `item-show.html` :

```txt
doctype
html
head
body
header
nav
main
footer
```

Vous vous concentrez uniquement sur le contenu du `<main>`.

---

## Contenu du main attendu

Le `<main>` du catalogue doit contenir :

```txt
h1 du catalogue
introduction courte
liste de plusieurs items
pour chaque item : titre, description courte, catégorie, thème, tags, lien détail
pagination fictive si utile
```

Chaque item doit être un `<article>`.

Une carte n’est pas encore un style visuel.

À cette étape, une “card” est d’abord une structure HTML répétable.

Exemple d’intention :

```txt
article
    titre avec lien
    description courte
    classification
    lien détail
```

Ne pensez pas encore :

```txt
grille
ombre
bordure
colonnes
alignement
hauteur égale
```

Ces questions viendront à l’étape CSS.

Pour l’instant, le composant card doit être correct sans apparence graphique.

---

## Point d’attention CSS

Le catalogue va naturellement apparaître comme une longue liste verticale.

C’est le bon comportement de départ.

N’essayez pas encore de faire une grille de cartes.

Si vous ressentez le besoin d’aligner les cartes en colonnes, notez ce besoin pour l’étape CSS, mais ne l’implémentez pas maintenant.

Le HTML doit d’abord prouver que chaque item reste lisible seul.

---

## Commit attendu

```txt
git add item-index.html
git commit -m "Add static item catalog page"
```

---

# 3. Créer `item-search.html`

## Objectif

La troisième page est la page de recherche et de filtres.

Fichier :

```txt
item-search.html
```

Cette page prépare :

```txt
la future route /item/search
la future lecture de $_GET
les filtres combinés
la recherche libre
le futur model item_search()
```

Elle explique aussi la surface de catalogage du projet.

Un item peut être retrouvé par :

```txt
recherche libre
catégorie
thème
tags
combinaison de plusieurs critères
```

---

## Contenu du main attendu

Le `<main>` doit contenir :

```txt
h1 de recherche
explication courte
formulaire GET
champ de recherche libre
filtres par catégories
filtres par thèmes
filtres par tags
bouton de recherche
zone de résultats fictifs
message de recherche vide ou sans résultat si utile
```

Ne pas utiliser de `<select>`.

Les filtres doivent rester visibles dans la page.

Utilisez des groupes de champs :

```txt
fieldset
legend
checkbox
radio si choix unique
label
```

Pour cette étape, privilégiez les `checkbox`, car les filtres peuvent se combiner.

Exemples de noms à prévoir :

```txt
q
categories[]
themes[]
tags[]
```

Cela prépare une URL future du type :

```txt
/item/search?q=mot&categories[]=x&themes[]=y&tags[]=z
```

---

## Point d’attention CSS

Un formulaire sans CSS sera vertical.

C’est normal.

Les `fieldset` auront une bordure par défaut.

C’est normal aussi.

Ne supprimez pas ces comportements.

Ils permettent de voir immédiatement quels champs appartiennent au même groupe.

Plus tard, le CSS pourra améliorer l’apparence.

Mais à cette étape, le regroupement doit déjà être compréhensible sans style.

---

## Commit attendu

```txt
git add item-search.html
git commit -m "Add static item search page"
```

---

# 4. Créer `home.html`

## Objectif

La quatrième page est la page d’accueil.

Fichier :

```txt
home.html
```

Elle arrive après les pages item parce qu’elle dépend de choix déjà faits :

```txt
ce qu’est un item
comment un item est résumé
comment on accède au catalogue
comment on présente une classification
comment on écrit un lien vers le détail
```

La page d’accueil est plus difficile qu’elle en a l’air.

Elle ne doit pas être une décoration vide.

Elle doit orienter l’utilisateur.

---

## Contenu du main attendu

Le `<main>` doit contenir :

```txt
h1 clair
présentation courte du site
lien principal vers le catalogue
quelques items mis en avant
explication de la catégorie ou du thème principal si utile
appel vers la recherche
appel vers la page à propos
```

Vous pouvez réutiliser la structure de card créée dans `item-index.html`.

Mais ne créez pas encore une nouvelle variante visuelle.

En HTML statique, un item mis en avant reste un contenu structuré.

---

## Point d’attention CSS

L’accueil donne souvent envie de faire du visuel trop tôt :

```txt
hero
colonnes
cartes alignées
grande image
boutons colorés
blocs côte à côte
```

Ne le faites pas maintenant.

Commencez par l’ordre du contenu.

Demandez-vous :

```txt
Que doit comprendre l’utilisateur en premier ?
Quelle action doit-il pouvoir faire ?
Quels items méritent d’être montrés ?
Pourquoi aller vers le catalogue ?
```

Si l’ordre est mauvais sans CSS, le CSS ne le réparera pas proprement.

---

## Commit attendu

```txt
git add home.html
git commit -m "Add static home page"
```

---

# 5. Créer `about.html`

## Objectif

La cinquième page est la page à propos.

Fichier :

```txt
about.html
```

Cette page remplace la page contact isolée.

Elle doit présenter le résultat des réflexions précédentes :

```txt
identité du projet
mission du site
public cible
ambiance
motto ou phrase de positionnement
valeurs
informations de contact
formulaire de contact
réseaux sociaux
```

Elle peut être complétée au fur et à mesure du projet.

C’est une page carte blanche, mais elle doit rester structurée.

---

## Contenu du main attendu

Le `<main>` doit contenir au minimum :

```txt
h1 À propos
présentation du projet
motto ou phrase courte
public cible
ce que le site propose
identité ou ambiance du projet
coordonnées ou informations de contact
liens vers réseaux sociaux
formulaire de contact
```

Le formulaire doit contenir :

```txt
nom
email
sujet
message
bouton d’envoi
```

Les réseaux sociaux peuvent être une simple liste de liens.

Exemple d’intention :

```txt
section présentation
section mission
section contact
section réseaux
```

Utilisez `address` si vous donnez des informations de contact.

---

## Point d’attention CSS

La page à propos est souvent l’endroit où on compense un manque de réflexion par une mise en page décorative.

À cette étape, elle doit surtout prouver que le projet est clair.

Pas besoin de mise en page spéciale.

Pas besoin de blocs colorés.

Pas besoin d’icônes.

Si le texte ne dit pas clairement ce qu’est le projet, le CSS ne pourra pas l’inventer.

---

## Commit attendu

```txt
git add about.html
git commit -m "Add static about page"
```

---

# Résultat final de l’étape HTML statique

À la fin de cette étape, vous devez avoir :

```txt
item-show.html
item-index.html
item-search.html
home.html
about.html
```

---

## Checklist finale

```txt
[ ] item-show.html existe.
[ ] item-index.html existe.
[ ] item-search.html existe.
[ ] home.html existe.
[ ] about.html existe.
[ ] Les pages sont reliées entre elles.
[ ] Aucun CSS n’est chargé.
[ ] Aucun <div> n’est utilisé.
[ ] Aucun style="" n’est utilisé.
[ ] Les formulaires ont des labels.
[ ] Les images ont des alt.
[ ] Les liens sont compréhensibles.
[ ] Le HTML reste lisible avec le style par défaut du navigateur.
```

---

## Erreurs bloquantes

Vous ne passez pas à l’étape suivante si :

```txt
un <div> est présent
du CSS est déjà chargé
un formulaire n’a pas de label
une image utile n’a pas de alt
les pages ne sont pas liées
le catalogue ne contient pas plusieurs items
la page détail ne montre pas catégorie, thème et tags
la page recherche ne permet pas de combiner les filtres
la page about ne présente pas l’identité du projet
```

---

## À savoir expliquer

Vous devez pouvoir répondre simplement :

```txt
Pourquoi commence-t-on par item-show.html ?
Pourquoi le catalogue vient après la page détail ?
Qu’est-ce qu’une card en HTML avant d’être une card en CSS ?
Pourquoi les filtres utilisent-ils des checkbox plutôt qu’un select ?
Que doit présenter la page about ?
Pourquoi le formulaire de contact est dans about.html ?
Pourquoi aucun CSS n’est autorisé à cette étape ?
Pourquoi les éléments de bloc se placent-ils déjà verticalement ?
Pourquoi display:flex n’est pas une réponse automatique ?
```

---

## Phrase à retenir

On ne stylise pas encore.

On regarde d’abord ce que le HTML sait déjà faire.
