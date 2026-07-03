# 05 — HTML valide et accessibilité minimale

## Objectif

Cette étape sert à vérifier, corriger et stabiliser les pages HTML statiques créées à l’étape précédente.

On ne crée pas encore de nouvelles fonctionnalités.

On ne travaille pas encore :

```txt
CSS
PHP dynamique
base de données
boucles
administration
JavaScript
```

On vérifie que les pages existantes sont :

```txt
valides
lisibles
sémantiques
accessibles au minimum
compréhensibles sans CSS
utilisables au clavier
prêtes pour l’étape CSS
```

Le but est simple :

```txt
ne pas styliser une structure fragile
ne pas dynamiser un HTML incorrect
ne pas transformer une erreur statique en erreur PHP répétée
```

Si le HTML est mauvais maintenant, il sera plus difficile à corriger plus tard, parce qu’il sera mélangé avec des views, des variables, des boucles et des conditions.

---

## Pages concernées

Vous devez vérifier les pages créées à l’étape précédente :

```txt
item-show.html
item-index.html
item-search.html
home.html
about.html
```

Chaque page doit être ouverte dans le navigateur et relue dans le code.

Cette étape n’est pas une étape de production rapide.

C’est une étape de correction.

---

## Règles de l’étape

Pendant toute cette étape, les règles de l’étape précédente restent valables :

```txt
aucun fichier CSS
aucune balise <style>
aucun attribut style=""
aucune classe CSS décorative
aucun display flex
aucun grid
aucun JavaScript
aucun PHP dynamique
aucune requête SQL
aucun <div>
```

Vous pouvez corriger :

```txt
la structure
les titres
les balises
les formulaires
les liens
les textes alternatifs
les noms d’id
l’ordre des contenus
la cohérence entre les pages
```

Vous ne pouvez pas corriger un problème de structure avec du style.

Mauvaise correction :

```html
<div class="main-title">Catalogue</div>
```

Bonne correction :

```html
<h1>Catalogue</h1>
```

Mauvaise correction :

```html
<span onclick="...">Envoyer</span>
```

Bonne correction :

```html
<button type="submit">Envoyer</button>
```

Mauvaise correction :

```html
<div class="navigation">
    <a href="home.html">Accueil</a>
</div>
```

Bonne correction :

```html
<nav aria-label="Navigation principale">
    <ul>
        <li><a href="home.html">Accueil</a></li>
    </ul>
</nav>
```

---

# 1. Vérifier que toutes les pages existent

## Objectif

Avant de corriger le détail, vérifiez que le socle est complet.

Vous devez avoir :

```txt
item-show.html
item-index.html
item-search.html
home.html
about.html
```

Toutes les pages doivent être reliées entre elles.

Depuis chaque page, l’utilisateur doit pouvoir retrouver au minimum :

```txt
Accueil
Catalogue
Recherche
À propos
```

La navigation principale doit être cohérente d’une page à l’autre.

Elle ne doit pas changer de nom ou d’ordre sans raison.

Exemple attendu :

```html
<nav aria-label="Navigation principale">
    <ul>
        <li><a href="home.html">Accueil</a></li>
        <li><a href="item-index.html">Catalogue</a></li>
        <li><a href="item-search.html">Recherche</a></li>
        <li><a href="about.html">À propos</a></li>
    </ul>
</nav>
```

---

## Validation

Ouvrez chaque page dans le navigateur.

Vérifiez :

```txt
la page s’ouvre
les liens de navigation fonctionnent
le lien vers le détail fonctionne
le lien retour catalogue fonctionne
la page recherche est accessible
la page à propos est accessible
aucun lien principal ne pointe vers un fichier absent
```

---

## Erreurs bloquantes

Vous ne continuez pas si :

```txt
une page manque
une page n’est pas liée aux autres
un lien principal est cassé
la navigation principale change sans raison entre les pages
le catalogue ne mène pas vers une page détail
la page détail ne permet pas de revenir au catalogue
```

---

# 2. Vérifier la structure minimale de chaque page

## Objectif

Chaque fichier HTML doit avoir une structure complète et correcte.

Chaque page doit contenir :

```txt
doctype
html lang="fr"
head
meta charset
meta viewport
title
body
header
nav
main
footer
```

Structure minimale attendue :

```html
<!doctype html>
<html lang="fr">
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Titre de la page — Nom du site</title>
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
        <h1>Titre principal de la page</h1>
    </main>

    <footer>
        <p>Nom du site — Projet ATE</p>
    </footer>
</body>
</html>
```

---

## Points à vérifier

```txt
Le doctype est présent.
La langue est indiquée avec lang="fr".
Le charset est utf-8.
Le viewport est présent.
Le title est spécifique à la page.
Le body contient les grandes zones.
Il y a un seul main.
Le footer existe.
```

Le contenu du `<title>` ne doit pas être identique partout.

Mauvais :

```html
<title>Document</title>
```

Mieux :

```html
<title>Catalogue — Nom du site</title>
```

```html
<title>Recherche — Nom du site</title>
```

```html
<title>À propos — Nom du site</title>
```

---

## Erreurs bloquantes

```txt
doctype absent
lang absent
title générique
viewport absent
body mal structuré
main absent
plusieurs main dans la même page
footer absent
```

---

# 3. Vérifier qu’il n’y a qu’un seul `<main>`

## Objectif

Le `<main>` représente le contenu principal unique de la page.

Il ne doit y en avoir qu’un seul par page.

La navigation, le header et le footer ne sont pas dans le `<main>`.

Correct :

```html
<body>
    <header>
        <nav aria-label="Navigation principale">
            ...
        </nav>
    </header>

    <main>
        <h1>Catalogue</h1>
        ...
    </main>

    <footer>
        ...
    </footer>
</body>
```

Incorrect :

```html
<body>
    <main>
        <header>...</header>
    </main>

    <main>
        <h1>Catalogue</h1>
    </main>
</body>
```

---

## Validation

Dans chaque fichier, cherchez :

```txt
<main
</main>
```

Vous devez trouver :

```txt
un seul <main>
une seule fermeture </main>
```

---

## Erreurs bloquantes

```txt
plusieurs main
main absent
navigation principale placée dans main
footer placé dans main sans raison
contenu principal hors main
```

---

# 4. Vérifier le `<h1>` et l’ordre des titres

## Objectif

Chaque page doit avoir un titre principal clair.

Chaque page doit contenir un seul `<h1>`.

Les autres titres doivent suivre une hiérarchie logique :

```txt
h1
    h2
        h3
```

Ne sautez pas directement de `h1` à `h4`.

Mauvais :

```html
<h1>Catalogue</h1>
<h4>Filtres</h4>
<h2>Résultats</h2>
```

Correct :

```html
<h1>Catalogue</h1>

<section aria-labelledby="filters-title">
    <h2 id="filters-title">Filtres</h2>
</section>

<section aria-labelledby="results-title">
    <h2 id="results-title">Résultats</h2>

    <article>
        <h3>Nom de l’item</h3>
    </article>
</section>
```

---

## Titres attendus par page

Pour `item-show.html` :

```txt
h1 = titre de l’item
h2 = Description
h2 = Classification
h2 = Informations
```

Pour `item-index.html` :

```txt
h1 = Catalogue
h2 = Liste des items ou Items disponibles
h3 = titre de chaque item
```

Pour `item-search.html` :

```txt
h1 = Recherche
h2 = Formulaire de recherche
h2 = Résultats
h3 = titre de chaque résultat fictif
```

Pour `home.html` :

```txt
h1 = titre clair du site ou proposition principale
h2 = Items mis en avant
h2 = Explorer le catalogue
h2 = À propos du projet
```

Pour `about.html` :

```txt
h1 = À propos
h2 = Présentation
h2 = Mission
h2 = Contact
h2 = Réseaux sociaux
```

Ces titres peuvent être adaptés au projet.

Mais la logique doit rester claire.

---

## Erreurs bloquantes

```txt
aucun h1
plusieurs h1
h1 vague
ordre des titres incohérent
titres utilisés seulement pour grossir du texte
sections sans titre identifiable
articles de catalogue sans titre
```

---

# 5. Vérifier les balises sémantiques

## Objectif

Le HTML doit décrire le rôle du contenu.

Il ne doit pas seulement créer des blocs.

À cette étape, les `<div>` sont toujours interdits.

Si un contenu existe, il doit avoir une balise qui correspond à son rôle.

---

## Choisir la bonne balise

Pour une zone de navigation :

```html
<nav aria-label="Navigation principale">
    ...
</nav>
```

Pour un item complet :

```html
<article>
    ...
</article>
```

Pour une zone thématique :

```html
<section aria-labelledby="section-title">
    <h2 id="section-title">Titre de la section</h2>
    ...
</section>
```

Pour une image avec légende :

```html
<figure>
    <img src="assets/img/item-placeholder.jpg" alt="Description précise de l’image">
    <figcaption>Image principale associée à l’item.</figcaption>
</figure>
```

Pour des métadonnées :

```html
<dl>
    <dt>Catégorie</dt>
    <dd>Nom de la catégorie</dd>

    <dt>Thème</dt>
    <dd>Nom du thème</dd>
</dl>
```

Pour des informations de contact :

```html
<address>
    <p>Email : <a href="mailto:contact@example.com">contact@example.com</a></p>
</address>
```

---

## Questions à poser devant chaque bloc

```txt
Est-ce une navigation ?
Est-ce le contenu principal ?
Est-ce un item autonome ?
Est-ce une section thématique ?
Est-ce une liste ?
Est-ce une définition ou une métadonnée ?
Est-ce une image avec légende ?
Est-ce une information de contact ?
Est-ce un formulaire ?
```

Si vous ne savez pas répondre, le contenu est probablement mal structuré.

---

## Erreurs bloquantes

```txt
présence d’un <div>
contenu principal non structuré
catalogue sans article
métadonnées écrites en paragraphes vagues
navigation sans nav
formulaire sans fieldset quand les groupes sont nécessaires
contact sans structure claire
```

---

# 6. Vérifier les formulaires

## Objectif

Un formulaire doit être utilisable sans CSS, sans JavaScript et sans explication orale.

Chaque champ doit avoir un label.

Chaque groupe de champs doit être compréhensible.

Les formulaires concernés sont :

```txt
item-search.html
about.html
```

---

## Règles obligatoires

Chaque champ doit avoir :

```txt
un id unique
un name utile
un label associé
un type adapté
```

Correct :

```html
<label for="contact-email">Email</label>
<input id="contact-email" name="email" type="email" required>
```

Incorrect :

```html
<input name="email" placeholder="Email">
```

Le `placeholder` ne remplace pas le label.

Il peut aider, mais il ne suffit pas.

---

## Recherche et filtres

Dans `item-search.html`, les filtres doivent être groupés.

Exemple :

```html
<form action="item-search.html" method="get">
    <section aria-labelledby="search-form-title">
        <h2 id="search-form-title">Formulaire de recherche</h2>

        <p>
            <label for="q">Recherche libre</label>
            <input id="q" name="q" type="search">
        </p>

        <fieldset>
            <legend>Catégories</legend>

            <p>
                <input id="category-example-1" name="categories[]" type="checkbox" value="categorie-1">
                <label for="category-example-1">Catégorie 1</label>
            </p>

            <p>
                <input id="category-example-2" name="categories[]" type="checkbox" value="categorie-2">
                <label for="category-example-2">Catégorie 2</label>
            </p>
        </fieldset>

        <fieldset>
            <legend>Thèmes</legend>

            <p>
                <input id="theme-example-1" name="themes[]" type="checkbox" value="theme-1">
                <label for="theme-example-1">Thème 1</label>
            </p>
        </fieldset>

        <fieldset>
            <legend>Tags</legend>

            <p>
                <input id="tag-example-1" name="tags[]" type="checkbox" value="tag-1">
                <label for="tag-example-1">Tag 1</label>
            </p>
        </fieldset>

        <button type="submit">Rechercher</button>
    </section>
</form>
```

---

## Formulaire de contact

Dans `about.html`, le formulaire de contact doit contenir :

```txt
nom
email
sujet
message
bouton d’envoi
```

Exemple :

```html
<form action="about.html" method="post">
    <fieldset>
        <legend>Envoyer un message</legend>

        <p>
            <label for="contact-name">Nom</label>
            <input id="contact-name" name="name" type="text" required>
        </p>

        <p>
            <label for="contact-email">Email</label>
            <input id="contact-email" name="email" type="email" required>
        </p>

        <p>
            <label for="contact-subject">Sujet</label>
            <input id="contact-subject" name="subject" type="text" required>
        </p>

        <p>
            <label for="contact-message">Message</label>
            <textarea id="contact-message" name="message" required></textarea>
        </p>

        <button type="submit">Envoyer</button>
    </fieldset>
</form>
```

Le formulaire ne sera pas encore traité.

C’est normal.

Il prépare seulement :

```txt
la future route /contact/create
le futur controller contact_create()
le futur model message_create()
la future table message
```

---

## Erreurs bloquantes

```txt
input sans label
label non relié au bon id
id dupliqué
name absent
placeholder utilisé comme seul label
checkbox sans label explicite
fieldset absent pour les groupes de filtres
bouton sans type
formulaire de contact incomplet
```

---

# 7. Vérifier les images

## Objectif

Chaque image utile doit avoir un texte alternatif.

Le `alt` ne décrit pas seulement le fichier.

Il doit décrire ce que l’image apporte à la page.

---

## Image utile

Si l’image aide à comprendre l’item, le `alt` doit être précis.

Mauvais :

```html
<img src="assets/img/item-placeholder.jpg" alt="image">
```

Mauvais :

```html
<img src="assets/img/item-placeholder.jpg" alt="photo">
```

Mieux :

```html
<img src="assets/img/item-placeholder.jpg" alt="Affiche du film présenté sur cette page">
```

Ou, pour un projet de recettes :

```html
<img src="assets/img/item-placeholder.jpg" alt="Assiette de pâtes aux légumes grillés">
```

Ou, pour un catalogue de jeux :

```html
<img src="assets/img/item-placeholder.jpg" alt="Boîte du jeu présenté dans le catalogue">
```

---

## Image décorative

À cette étape, évitez les images purement décoratives.

Si une image n’apporte aucune information, demandez-vous pourquoi elle est déjà présente.

Plus tard, le CSS pourra gérer des éléments visuels décoratifs.

Pour le moment, les images doivent servir le contenu.

---

## `figure` et `figcaption`

Si l’image a une légende, utilisez :

```html
<figure>
    <img src="assets/img/item-placeholder.jpg" alt="Description utile de l’image">
    <figcaption>Légende de l’image.</figcaption>
</figure>
```

Le `alt` et le `figcaption` ne doivent pas être des copies inutiles.

Mauvais :

```html
<img src="affiche.jpg" alt="Affiche">
<figcaption>Affiche</figcaption>
```

Mieux :

```html
<img src="affiche.jpg" alt="Affiche du film montrant le personnage principal dans une rue de nuit">
<figcaption>Affiche principale du film.</figcaption>
```

---

## Erreurs bloquantes

```txt
image utile sans alt
alt vide sur une image informative
alt vague
alt identique au nom du fichier
figcaption qui répète inutilement le alt
image décorative utilisée pour compenser un contenu faible
```

---

# 8. Vérifier les liens

## Objectif

Un lien doit être compréhensible même s’il est lu hors contexte.

Mauvais :

```html
<a href="item-show.html">Cliquez ici</a>
```

Mauvais :

```html
<a href="item-show.html">Lire plus</a>
```

Mieux :

```html
<a href="item-show.html">Voir le détail de Nom de l’item</a>
```

Mieux :

```html
<a href="item-index.html">Retour au catalogue</a>
```

Mieux :

```html
<a href="item-search.html">Rechercher un item</a>
```

---

## Liens attendus

Dans `item-show.html` :

```txt
retour catalogue
recherche
navigation principale
```

Dans `item-index.html` :

```txt
lien détail pour chaque item
recherche
navigation principale
pagination fictive si présente
```

Dans `item-search.html` :

```txt
retour catalogue
lien vers les résultats fictifs si utile
navigation principale
```

Dans `home.html` :

```txt
lien principal vers catalogue
lien vers recherche
lien vers à propos
liens vers items mis en avant
```

Dans `about.html` :

```txt
liens réseaux sociaux
email si présent
navigation principale
```

---

## Erreurs bloquantes

```txt
lien “cliquez ici”
lien “en savoir plus” répété plusieurs fois sans contexte
href vide
href="#"
lien vers un fichier absent
lien détail identique pour tous les items sans intention claire
email non cliquable si une adresse est affichée
```

---

# 9. Vérifier les identifiants `id`

## Objectif

Un `id` doit être unique dans une page.

Les `id` servent surtout à :

```txt
relier un label à un champ
relier une section à son titre avec aria-labelledby
créer des ancres internes
```

Ils ne doivent pas être copiés plusieurs fois.

---

## Exemple correct

```html
<section aria-labelledby="classification-title">
    <h2 id="classification-title">Classification</h2>
    ...
</section>
```

```html
<label for="contact-email">Email</label>
<input id="contact-email" name="email" type="email">
```

---

## Exemple incorrect

```html
<label for="email">Email</label>
<input id="email" name="email" type="email">

<label for="email">Email de confirmation</label>
<input id="email" name="email_confirmation" type="email">
```

Correction :

```html
<label for="contact-email">Email</label>
<input id="contact-email" name="email" type="email">

<label for="contact-email-confirmation">Email de confirmation</label>
<input id="contact-email-confirmation" name="email_confirmation" type="email">
```

---

## Convention conseillée

Utilisez des préfixes liés au contexte :

```txt
contact-name
contact-email
contact-message

search-q
search-category-film
search-theme-history
search-tag-featured

item-description-title
item-classification-title
item-metadata-title
```

---

## Erreurs bloquantes

```txt
id dupliqué
label for qui pointe vers un id inexistant
aria-labelledby qui pointe vers un id inexistant
id vague copié partout
id utilisé comme classe CSS future
```

---

# 10. Vérifier l’accessibilité minimale sans CSS

## Objectif

La page doit rester utilisable avec le comportement naturel du navigateur.

À cette étape, l’accessibilité minimale repose surtout sur :

```txt
structure HTML correcte
navigation clavier
ordre de lecture logique
liens visibles
focus visible par défaut
labels
textes alternatifs
formulaires compréhensibles
```

On n’ajoute pas encore du CSS pour corriger le focus.

On vérifie d’abord que rien ne l’empêche.

---

## Test clavier

Pour chaque page :

```txt
ouvrez la page dans le navigateur
appuyez sur Tab
continuez jusqu’au footer
utilisez Shift + Tab pour revenir en arrière
utilisez Enter sur les liens
utilisez Space sur les checkbox
utilisez Tab dans les formulaires
```

Vous devez observer :

```txt
les liens reçoivent le focus
les champs reçoivent le focus
les boutons reçoivent le focus
l’ordre du focus suit l’ordre de lecture
les checkbox peuvent être cochées au clavier
le bouton du formulaire peut être atteint
```

Si vous ne voyez pas où vous êtes pendant la navigation au clavier, c’est un problème.

À cette étape, le navigateur affiche normalement un focus par défaut.

Ne le supprimez pas.

---

## Ordre de lecture

L’ordre du HTML doit correspondre à l’ordre logique de lecture.

Correct :

```txt
titre
introduction
formulaire
résultats
navigation complémentaire
```

Mauvais :

```txt
résultats
footer
titre
formulaire
navigation
```

Le CSS pourra plus tard modifier l’apparence.

Mais le HTML doit rester logique dans son ordre source.

---

## ARIA

N’ajoutez pas des attributs ARIA au hasard.

ARIA sert à compléter une structure correcte.

ARIA ne sert pas à cacher une mauvaise structure.

Mauvais réflexe :

```html
<div role="button">Envoyer</div>
```

Bonne structure :

```html
<button type="submit">Envoyer</button>
```

Mauvais réflexe :

```html
<div role="navigation">
    ...
</div>
```

Bonne structure :

```html
<nav aria-label="Navigation principale">
    ...
</nav>
```

Utilisez `aria-label` ou `aria-labelledby` seulement quand cela clarifie réellement la page.

Exemples utiles :

```html
<nav aria-label="Navigation principale">
    ...
</nav>
```

```html
<nav aria-label="Navigation de l’item">
    ...
</nav>
```

```html
<section aria-labelledby="results-title">
    <h2 id="results-title">Résultats</h2>
    ...
</section>
```

---

## Erreurs bloquantes

```txt
éléments interactifs impossibles à atteindre au clavier
ordre de tabulation incohérent
checkbox sans label
bouton remplacé par un span ou un faux lien
aria-label utilisé pour compenser un mauvais HTML
navigation non identifiable
focus invisible ou supprimé
```

---

# 11. Vérifier que la page reste compréhensible sans CSS

## Objectif

Le style par défaut du navigateur doit déjà permettre de comprendre la page.

Sans CSS, vous devez distinguer :

```txt
le titre principal
les sections
les articles
les listes
les formulaires
les groupes de champs
les liens
les images
les métadonnées
```

Si tout semble être une suite de texte sans structure, le HTML n’est pas assez clair.

---

## Ce qu’il faut observer

Dans `item-show.html` :

```txt
le titre de l’item est évident
la description est séparée des métadonnées
la classification est identifiable
les informations sont lisibles
le retour catalogue est visible
```

Dans `item-index.html` :

```txt
chaque item est distinct
chaque item a un titre
chaque item a un lien détail
les métadonnées sont lisibles
```

Dans `item-search.html` :

```txt
le formulaire est compréhensible
les groupes de filtres sont visibles
les résultats fictifs sont séparés du formulaire
```

Dans `home.html` :

```txt
le site est compréhensible immédiatement
l’action principale est claire
les items mis en avant ne ressemblent pas à du texte perdu
```

Dans `about.html` :

```txt
le projet est expliqué
le contact est identifiable
le formulaire est utilisable
les liens sociaux sont lisibles
```

---

## Erreurs bloquantes

```txt
contenu sans structure visible
formulaire difficile à comprendre sans CSS
items impossibles à distinguer
liens perdus dans le texte
métadonnées confuses
page d’accueil décorative mais peu informative
page à propos vague
```

---

# 12. Valider le HTML avec un outil

## Objectif

La lecture humaine ne suffit pas.

Vous devez aussi faire valider le HTML par un outil.

Utilisez un validateur HTML.

Pour chaque page, vérifiez :

```txt
balises mal fermées
attributs invalides
id dupliqués
éléments mal placés
formulaires incorrects
structure HTML invalide
```

---

## Méthode

Pour chaque fichier :

```txt
item-show.html
item-index.html
item-search.html
home.html
about.html
```

Faites une validation.

Corrigez les erreurs.

Relancez la validation.

Ne vous contentez pas de corriger la première erreur visible.

Une erreur HTML peut provoquer plusieurs erreurs en cascade.

---

## Résultat attendu

À la fin :

```txt
chaque page passe la validation HTML
ou chaque erreur restante est comprise et justifiée
```

Dans ce projet, les erreurs non comprises ne sont pas acceptées.

---

## Erreurs bloquantes

```txt
balises non fermées
mauvais imbriquement
id dupliqué
attribut invalide
formulaire invalide
erreur du validateur ignorée
erreur laissée sans explication
```

---

# 13. Corriger sans réécrire au hasard

## Objectif

Cette étape ne sert pas à refaire toutes les pages.

Elle sert à corriger proprement.

Procédez par petites corrections.

Ordre conseillé :

```txt
structure globale
main unique
h1 et titres
navigation
sections
articles
formulaires
images
liens
id
validation outil
test clavier
```

Ne corrigez pas tout en même temps.

Chaque correction doit être vérifiable.

---

## Méthode de travail

Pour chaque page :

```txt
ouvrir la page
lire la structure
corriger le code
tester dans le navigateur
valider avec un outil
tester au clavier
committer
```

---

## Commits attendus

Vous pouvez faire un commit par page :

```txt
git add item-show.html
git commit -m "Validate item detail HTML"
```

```txt
git add item-index.html
git commit -m "Validate item catalog HTML"
```

```txt
git add item-search.html
git commit -m "Validate item search HTML"
```

```txt
git add home.html
git commit -m "Validate home HTML"
```

```txt
git add about.html
git commit -m "Validate about HTML"
```

Ou un commit global si toutes les corrections sont petites :

```txt
git add item-show.html item-index.html item-search.html home.html about.html
git commit -m "Validate static frontend HTML"
```

---

# Résultat final de l’étape

À la fin de cette étape, vous devez avoir :

```txt
5 pages HTML statiques
une navigation cohérente
un HTML valide
une structure sémantique
des formulaires avec labels
des images avec alt utiles
des liens compréhensibles
des id uniques
une navigation clavier fonctionnelle
des pages compréhensibles sans CSS
```

Vous êtes alors prêt à passer au CSS.

Pas avant.

---

## Checklist finale

```txt
[ ] item-show.html est valide.
[ ] item-index.html est valide.
[ ] item-search.html est valide.
[ ] home.html est valide.
[ ] about.html est valide.

[ ] Chaque page a un doctype.
[ ] Chaque page a lang="fr".
[ ] Chaque page a un title spécifique.
[ ] Chaque page a meta charset.
[ ] Chaque page a meta viewport.

[ ] Chaque page contient un seul main.
[ ] Chaque page contient un seul h1.
[ ] Les titres suivent un ordre logique.
[ ] Les sections importantes ont un titre.
[ ] Les articles du catalogue ont un titre.

[ ] Aucun div n’est présent.
[ ] Aucun style="" n’est présent.
[ ] Aucune balise style n’est présente.
[ ] Aucun fichier CSS n’est chargé.
[ ] Aucun JavaScript n’est chargé.

[ ] La navigation principale est cohérente.
[ ] Les pages sont reliées entre elles.
[ ] Aucun lien principal n’est cassé.
[ ] Les liens sont compréhensibles.

[ ] Tous les formulaires ont des labels.
[ ] Tous les labels sont reliés au bon champ.
[ ] Les fieldset ont des legend.
[ ] Les boutons ont un type.
[ ] Les name des champs sont utiles.

[ ] Les images utiles ont un alt utile.
[ ] Les métadonnées utilisent une structure adaptée.
[ ] Les id sont uniques.
[ ] Les aria-labelledby pointent vers des id existants.

[ ] La navigation au clavier fonctionne.
[ ] L’ordre de tabulation est logique.
[ ] Les champs et boutons sont atteignables.
[ ] Les checkbox sont utilisables au clavier.
[ ] Le focus reste visible.

[ ] Chaque page reste compréhensible sans CSS.
[ ] Les erreurs du validateur sont corrigées.
```

---

## Erreurs bloquantes

Vous ne passez pas à l’étape CSS si :

```txt
une page HTML est invalide
un <div> est présent
une page contient plusieurs main
une page n’a pas de h1
les titres sont incohérents
la navigation est cassée
un formulaire a un champ sans label
un label pointe vers un mauvais id
un fieldset n’a pas de legend
une image utile n’a pas de alt
un lien est vague ou cassé
un id est dupliqué
un élément interactif n’est pas atteignable au clavier
la page n’est pas compréhensible sans CSS
un problème est corrigé avec ARIA au lieu d’être corrigé avec une bonne balise
une erreur du validateur est ignorée
```

---

## À savoir expliquer

Vous devez pouvoir répondre simplement :

```txt
Pourquoi valide-t-on le HTML avant d’écrire le CSS ?
Pourquoi une page doit-elle avoir un seul main ?
Pourquoi un h1 clair est-il important ?
Pourquoi l’ordre des titres compte-t-il ?
Pourquoi un label est-il obligatoire pour un champ ?
Pourquoi le placeholder ne remplace-t-il pas un label ?
Pourquoi les fieldset et legend sont-ils utiles dans la recherche ?
Pourquoi chaque id doit-il être unique ?
Pourquoi un lien “cliquez ici” est-il mauvais ?
À quoi sert le alt d’une image ?
Pourquoi ne faut-il pas ajouter ARIA partout ?
Comment tester une page au clavier ?
Pourquoi la page doit-elle rester compréhensible sans CSS ?
Pourquoi une erreur HTML statique devient-elle plus grave en PHP ?
```

---

## Phrase à retenir

On ne corrige pas le HTML avec du CSS.

On corrige le HTML avec du HTML.
