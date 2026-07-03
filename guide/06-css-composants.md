# 06 — CSS et composants

## Objectif

Cette étape sert à ajouter le CSS sur une base HTML déjà propre.

On ne corrige pas encore :

```txt
la structure HTML
les titres
les liens
les formulaires
les textes alternatifs
la navigation
l’accessibilité minimale
```

Ces points ont été réglés à l’étape précédente.

Le CSS ne sert pas à sauver un HTML fragile.

Le CSS sert à :

```txt
organiser visuellement l’existant
rendre les pages lisibles sur mobile et desktop
stabiliser les composants communs
donner une cohérence graphique au projet
préparer la future transformation en views PHP
```

Le travail CSS commence maintenant, mais il reste sobre.

On ne cherche pas encore :

```txt
effets avancés
animations complexes
framework CSS
JavaScript
menu hamburger
composants interactifs riches
administration
PHP dynamique
base de données
```

Le but est d’obtenir une interface claire, stable et réutilisable.

---

## Pages concernées

Toutes les pages reçoivent le CSS commun :

```txt
item-show.html
item-index.html
item-search.html
home.html
about.html
```

Mais le travail détaillé se fait dans cet ordre :

```txt
1. éléments communs hors main
2. item-show.html
3. item-index.html
4. home.html
```

Les pages `item-search.html` et `about.html` doivent rester lisibles grâce au style global.

Elles pourront recevoir un traitement plus précis plus tard, quand les formulaires et le contact seront repris dynamiquement.

---

## Règle principale de l’étape

On agence l’existant.

On ne force pas la page avec des artifices.

À cette étape, vous ne devez pas utiliser :

```txt
float
position absolute pour faire le layout
position fixed pour compenser une mauvaise structure
position relative partout
hauteurs fixes inutiles
largeurs fixes rigides
marges négatives
div ajoutés pour décorer
CSS inline
```

Le CSS doit partir de la structure HTML existante.

La question à poser devant chaque choix CSS est :

```txt
Quel contenu existe déjà ?
Quel est son rôle ?
Doit-il rester dans le flux naturel ?
Doit-il être aligné sur un axe ?
Doit-il être organisé en grille ?
```

---

# 1. Créer et relier le fichier CSS

## Objectif

Toutes les pages doivent charger le même fichier CSS principal.

Créez :

```txt
assets/css/app.css
```

Dans chaque page HTML, ajoutez dans le `<head>` :

```html
<link rel="stylesheet" href="assets/css/app.css">
```

Le chemin peut être adapté si votre arborescence est différente.

Mais il doit être cohérent sur toutes les pages.

---

## Règles

Un seul fichier CSS principal suffit à cette étape.

Ne créez pas encore :

```txt
home.css
catalog.css
detail.css
mobile.css
desktop.css
reset.css complexe
theme-dark.css
animations.css
```

Le projet est encore statique.

Il doit rester facile à lire.

---

## Validation

Ouvrez chaque page dans le navigateur.

Modifiez temporairement une règle simple dans `app.css`, par exemple la police générale ou la couleur du texte.

Vérifiez que toutes les pages sont touchées.

---

## Erreurs bloquantes

Vous ne continuez pas si :

```txt
le fichier CSS n’est pas chargé
certaines pages ne chargent pas le CSS
chaque page utilise un fichier CSS différent
le CSS est écrit dans une balise <style>
le CSS est écrit avec style=""
le chemin vers le fichier CSS est cassé
```

---

# 2. Comprendre les trois modes de layout

## Objectif

Avant d’écrire les composants, vous devez comprendre les trois manières principales d’agencer une page.

Dans ce projet, vous utiliserez surtout :

```txt
flux naturel
flex
grid
```

Le bon CSS vient souvent du bon choix entre ces trois possibilités.

---

## 2.1 Flux naturel

Le flux naturel est le comportement normal du HTML.

Les éléments apparaissent dans l’ordre du document.

Le texte se lit de haut en bas.

Les titres introduisent les sections.

Les paragraphes se suivent.

Les listes restent des listes.

C’est le point de départ.

Le flux naturel convient pour :

```txt
texte long
description
contenu d’un article
sections successives
formulaires simples
footer simple
page mobile
```

Ne cherchez pas à tout transformer en flex ou en grid.

Une bonne page mobile peut souvent commencer par un flux naturel très simple.

---

## 2.2 Flex

Flex sert à aligner des éléments sur un axe principal.

Il est utile quand des éléments doivent être :

```txt
sur une ligne
sur une colonne
espacés régulièrement
centrés
alignés verticalement
répartis dans un composant
renvoyés à la ligne si nécessaire
```

Flex convient pour :

```txt
navigation
groupe de liens
groupe de boutons
actions d’une carte
petite liste de badges
alignement interne d’un composant
```

Flex n’est pas le meilleur outil pour construire toute une page.

Flex est surtout utile à l’intérieur d’un composant.

---

## 2.3 Grid

Grid sert à organiser des zones sur deux axes.

Il est utile quand vous devez gérer :

```txt
colonnes
lignes
grille de cartes
layout général d’une page
répartition principale d’un contenu
zone image + zone texte
résultats de catalogue
```

Grid convient pour :

```txt
page détail sur desktop
grille de catalogue
sections de home
dashboard plus tard
```

Grid ne doit pas être utilisé pour tout.

Un paragraphe n’a pas besoin de grid.

Une navigation simple n’a souvent pas besoin de grid.

---

## 2.4 Combinaison judicieuse

La combinaison la plus fréquente est :

```txt
flux naturel pour le contenu
grid pour les grandes zones
flex pour l’intérieur des composants
```

Exemple de raisonnement :

```txt
La page détail a une grande zone image + texte.
→ grid peut être utile sur desktop.

Dans la zone texte, les paragraphes se lisent normalement.
→ flux naturel.

Les tags sont sur une ligne et peuvent revenir à la ligne.
→ flex peut être utile.
```

Autre exemple :

```txt
Le catalogue affiche plusieurs items.
→ grid pour la liste de cartes.

Chaque carte contient un titre, une description, des métadonnées et un lien.
→ flux naturel dans la carte.

Les actions de la carte doivent être alignées.
→ flex peut être utile pour les actions.
```

---

## Erreurs bloquantes

```txt
tout mettre en display flex
tout mettre en display grid
utiliser position pour créer les colonnes
utiliser float pour placer une image
casser l’ordre de lecture logique
faire dépendre le layout d’une hauteur fixe
masquer un problème de structure avec du CSS
```

---

# 3. Poser les variables et les bases

## Objectif

Avant les composants, définissez les valeurs communes.

Ces valeurs doivent venir de la direction graphique définie plus tôt.

Vous devez au minimum prévoir :

```txt
couleur de fond
couleur du texte
couleur principale
couleur secondaire
couleur de bordure
espacements
largeur maximale de lecture
rayon éventuel
police de base
```

Exemple minimal :

```css
:root {
    --color-bg: #ffffff;
    --color-text: #111111;
    --color-primary: #3344ff;
    --space: 1rem;
}
```

Ce n’est pas une charte complète.

C’est un point de départ commun.

---

## Règles

Les variables ne doivent pas être décoratives au hasard.

Chaque variable doit avoir un rôle.

Mauvais :

```txt
--blue1
--blue2
--blue3
--nice-color
--random-space
```

Mieux :

```txt
--color-bg
--color-text
--color-primary
--color-muted
--color-border
--space-s
--space-m
--space-l
```

---

## Base de page

Réglez d’abord les éléments généraux :

```txt
body
img
a
button
input
textarea
select
```

Règles importantes :

```txt
les images ne doivent pas dépasser leur conteneur
le texte doit rester lisible
les liens doivent rester identifiables
le focus ne doit pas disparaître
les champs doivent être utilisables
```

Exemple ponctuel :

```css
img {
    max-width: 100%;
    height: auto;
}
```

---

## Validation

Vérifiez sur toutes les pages :

```txt
le texte est lisible
les images ne débordent pas
les liens sont visibles
les champs restent utilisables
le focus clavier reste visible
la page ne crée pas de scroll horizontal
```

---

## Erreurs bloquantes

```txt
couleurs illisibles
texte trop petit
image qui déborde
focus supprimé
lien impossible à distinguer
scroll horizontal sur mobile
variables inutilisées
valeurs copiées partout au lieu d’être centralisées
```

---

# 4. Régler d’abord ce qui est commun

## Objectif

Avant de styliser les pages une par une, stabilisez ce qui revient partout.

Cela concerne surtout ce qui est hors du `<main>` :

```txt
body
header
nom du site
navigation principale
footer
largeur générale
espacement entre les grandes zones
```

Le CSS doit émerger des points communs.

On ne commence pas par la page la plus décorative.

On commence par ce qui structure toutes les pages.

---

## Layout global

Le layout global doit rester simple.

La page doit avoir :

```txt
un haut identifiable
une navigation lisible
un contenu principal centré ou cadré
un footer clair
un rythme vertical régulier
```

À cette étape, il est souvent suffisant d’avoir :

```txt
body en flux naturel
header stylé simplement
main avec une largeur maximale
footer séparé clairement
```

Le `main` ne doit pas être collé aux bords de l’écran.

Le contenu ne doit pas devenir trop large sur desktop.

---

## Header

Le header sert à identifier le site.

Il doit contenir :

```txt
nom du site
navigation principale
```

Il ne doit pas devenir une affiche graphique complexe.

Particularités à comprendre :

```txt
le header apparaît sur toutes les pages
il donne la première impression
il doit rester lisible sur mobile
il ne doit pas prendre toute la hauteur
il ne doit pas masquer le contenu
```

Ne faites pas un header fixe.

Ne faites pas un menu qui cache le contenu.

Ne faites pas un layout dépendant de `position`.

---

## Navigation

La navigation est une liste de liens.

Elle doit rester une liste de liens.

Le CSS peut l’aligner, l’espacer, la rendre plus claire.

Mais il ne doit pas retirer sa compréhension.

Flex est souvent adapté ici.

Pourquoi ?

```txt
les liens sont sur un axe
ils peuvent s’aligner
ils peuvent revenir à la ligne
ils doivent rester lisibles
```

Exemple ponctuel :

```css
.site-nav ul {
    display: flex;
    flex-wrap: wrap;
    gap: var(--space);
}
```

Ce type de règle est acceptable.

Il ne transforme pas la navigation en décor.

Il agence les liens existants.

---

## Footer

Le footer doit rester simple.

Il sert à clôturer la page.

Il peut contenir :

```txt
nom du projet
mention ATE
liens secondaires
contact
```

Particularités à comprendre :

```txt
le footer ne doit pas voler l’attention du main
il doit rester lisible
il doit être cohérent sur toutes les pages
il doit fonctionner avec peu ou beaucoup de contenu
```

Le footer n’a pas besoin d’être complexe.

Un bon footer simple vaut mieux qu’un grand bloc décoratif inutile.

---

## Validation

Vérifiez toutes les pages.

Vous devez obtenir :

```txt
même header
même navigation
même footer
même rythme général
même largeur de contenu
même traitement des liens
même traitement du focus
```

La page ne doit pas donner l’impression d’avoir cinq sites différents.

---

## Erreurs bloquantes

```txt
header différent selon les pages
navigation qui change sans raison
footer absent ou incohérent
menu illisible sur mobile
menu qui sort de l’écran
position fixed utilisée sans nécessité
liens de navigation non visibles
focus invisible dans la navigation
main trop large sur desktop
main collé aux bords sur mobile
```

---

# 5. Ajouter les classes nécessaires, sans salir le HTML

## Objectif

Le HTML était volontairement sobre.

À l’étape CSS, vous pouvez ajouter des classes.

Mais vous ne devez pas transformer le HTML en décor.

Les classes doivent nommer des rôles de composants.

---

## Bon usage des classes

Exemples de classes utiles :

```txt
site-header
site-nav
site-footer
item-detail
item-meta
item-grid
item-card
tag-list
tag-badge
button
button-primary
```

Ces classes indiquent un rôle.

Elles peuvent être réutilisées.

---

## Mauvais usage des classes

Évitez :

```txt
blue
big
left
right
box1
box2
pretty
centered
margin-top-large
```

Ces classes décrivent une apparence ponctuelle.

Elles ne décrivent pas un composant.

---

## Règle

Ajoutez une classe seulement si elle aide à :

```txt
identifier un composant
réutiliser un style
limiter les sélecteurs complexes
clarifier le CSS
```

N’ajoutez pas des classes partout.

---

## Validation

Relisez vos classes.

Pour chaque classe, demandez :

```txt
Quel composant nomme-t-elle ?
Est-elle réutilisable ?
Est-elle compréhensible dans trois semaines ?
Est-elle liée au rôle du contenu plutôt qu’à une décoration ponctuelle ?
```

---

## Erreurs bloquantes

```txt
classes décoratives partout
classes vagues
classes contradictoires
classes différentes pour le même composant
sélecteurs CSS trop longs
HTML rempli de classes inutiles
ajout de div pour créer des boîtes
```

---

# 6. Travailler `item-show.html` : layout général

## Objectif

La page détail est la première page à travailler en profondeur.

Pourquoi elle d’abord ?

Parce qu’elle permet de régler le layout général d’un contenu complet.

Elle contient généralement :

```txt
titre
image principale
description
classification
métadonnées
tags
lien retour catalogue
```

Cette page montre comment organiser un contenu riche sans perdre la lecture.

---

## Principe

Sur mobile, la page détail doit rester en flux naturel.

Ordre conseillé :

```txt
titre
image
description
classification
informations
tags
navigation de retour
```

Sur desktop, certains contenus peuvent être placés en colonnes.

Par exemple :

```txt
colonne principale : titre, image, description
colonne secondaire : classification, métadonnées, tags
```

Grid peut être utile ici.

Mais seulement si le contenu justifie deux zones.

---

## Composant : détail d’item

Le composant principal peut être nommé :

```txt
item-detail
```

Il représente la fiche complète d’un item.

Particularités à comprendre :

```txt
le titre doit rester prioritaire
l’image ne doit pas écraser le texte
la description doit garder une largeur lisible
les métadonnées doivent être distinctes du contenu principal
les tags doivent rester lisibles
le retour catalogue doit rester accessible
```

---

## Composant : média principal

L’image principale doit être stable.

Elle ne doit pas :

```txt
déborder
être déformée
forcer une hauteur fixe absurde
pousser le texte hors écran
```

Si vous utilisez `object-fit`, comprenez ce que vous faites.

`object-fit: cover` peut couper l’image.

C’est parfois acceptable pour une carte.

C’est plus délicat pour une page détail, où l’image peut avoir une valeur informative.

---

## Composant : métadonnées

Les métadonnées peuvent rester en `<dl>`.

Le CSS peut améliorer leur lisibilité.

Ne transformez pas les métadonnées en paragraphes dispersés.

Particularités à comprendre :

```txt
dt indique le nom de l’information
dd indique la valeur
la relation doit rester visible
les informations doivent être scannables
```

Grid peut être utile pour un `<dl>` court.

Mais le contenu doit rester compréhensible si la grille disparaît.

---

## Composant : tags

Les tags doivent rester des informations, pas seulement des décorations.

Ils peuvent être affichés comme des badges.

Flex est souvent adapté :

```txt
plusieurs tags sur une ligne
retour à la ligne si nécessaire
espacement régulier
```

Un tag ne doit pas devenir illisible pour ressembler à un bouton.

S’il n’est pas cliquable, ne le stylisez pas comme une action principale.

---

## Validation de `item-show.html`

Vérifiez :

```txt
la page reste lisible sur mobile
le titre de l’item est évident
l’image ne déborde pas
la description garde une bonne largeur
les métadonnées sont distinctes
les tags sont lisibles
le lien retour catalogue est visible
le layout desktop améliore la lecture sans changer le sens
aucun contenu important n’est masqué
```

---

## Erreurs bloquantes

```txt
image déformée
texte trop large sur desktop
layout en deux colonnes cassé sur mobile
métadonnées confuses
tags illisibles
utilisation de float pour placer l’image
utilisation de position pour créer les colonnes
ordre visuel incohérent avec l’ordre HTML
retour catalogue difficile à trouver
```

---

# 7. Travailler `item-index.html` : grille de résultats

## Objectif

La page catalogue sert à afficher une collection d’items.

Elle doit permettre de parcourir plusieurs résultats rapidement.

C’est ici que la grille devient importante.

---

## Principe

Le catalogue contient généralement :

```txt
titre de page
introduction courte
liste d’items
cartes répétées
pagination éventuelle
liens vers les détails
```

La liste des items doit être claire.

Chaque item doit être identifiable comme une unité autonome.

Grid est souvent l’outil principal pour la liste de résultats.

---

## Composant : grille de résultats

Le composant peut être nommé :

```txt
item-grid
```

Il organise plusieurs cartes.

Particularités à comprendre :

```txt
une colonne sur petit écran
plusieurs colonnes quand l’espace augmente
espacement régulier entre les cartes
cartes qui restent lisibles
pas de largeur fixe rigide
pas de débordement horizontal
```

Exemple ponctuel :

```css
.item-grid {
    display: grid;
    gap: var(--space);
}
```

Puis, à partir d’une largeur suffisante, on peut augmenter le nombre de colonnes.

L’idée n’est pas de forcer trois colonnes partout.

L’idée est de laisser l’espace disponible guider la grille.

---

## Composant : carte item

Le composant peut être nommé :

```txt
item-card
```

Une carte représente un item dans une liste.

Elle doit contenir au minimum :

```txt
titre
description courte
catégorie ou thème
tags éventuels
lien vers le détail
image éventuelle
```

Particularités à comprendre :

```txt
la carte doit être scannable
le titre doit dominer
la description doit rester courte
le lien détail doit être clair
les métadonnées doivent être visibles mais secondaires
les cartes doivent se ressembler
```

Une carte n’est pas une affiche.

Une carte est un résumé utilisable.

---

## Layout interne de la carte

À l’intérieur de la carte, le flux naturel suffit souvent.

Ordre conseillé :

```txt
image
titre
description
métadonnées
tags
action
```

Flex peut être utile pour :

```txt
aligner une petite liste de tags
placer plusieurs actions
gérer une ligne de métadonnées courte
```

Grid peut être utile si la carte a une structure régulière.

Mais ne compliquez pas la carte avant qu’elle existe clairement.

---

## Hauteur des cartes

Ne commencez pas par forcer toutes les cartes à la même hauteur.

Une hauteur fixe peut créer :

```txt
texte coupé
espaces vides absurdes
cartes cassées sur mobile
problèmes d’accessibilité
```

Si vous voulez harmoniser les cartes, travaillez d’abord :

```txt
espacements
ordre interne
longueur des textes
cohérence des images
```

L’alignement parfait vient après la lisibilité.

---

## Images dans les cartes

Dans une carte, une image peut être recadrée plus facilement que sur une page détail.

Mais le recadrage doit rester raisonnable.

Particularités à comprendre :

```txt
une image de carte sert à identifier vite l’item
elle ne doit pas dominer tout le contenu
elle doit garder une proportion stable
elle ne doit pas ralentir la lecture
```

---

## Pagination

Si une pagination fictive existe, elle doit rester claire.

Flex est souvent adapté pour une pagination simple :

```txt
liens alignés
espacés
retour à la ligne possible
page active visible
```

La page active ne doit pas être indiquée seulement par la couleur.

---

## Validation de `item-index.html`

Vérifiez :

```txt
le catalogue reste lisible sur mobile
la grille ne déborde pas
chaque carte est distincte
chaque carte a un titre visible
chaque carte a un lien détail compréhensible
les cartes ont une logique commune
les images ne sont pas déformées
les tags restent lisibles
la pagination est utilisable si elle existe
```

---

## Erreurs bloquantes

```txt
grille cassée sur mobile
cartes trop étroites
cartes trop larges
cartes non distinguables
titre de carte peu visible
lien “lire plus” répété sans contexte
images déformées
hauteurs fixes qui coupent le contenu
pagination illisible
scroll horizontal
```

---

# 8. Travailler `home.html` : composants uniques et expérimentation modeste

## Objectif

La page d’accueil peut être plus expressive.

Mais elle ne doit pas être un laboratoire incontrôlé.

Elle doit :

```txt
présenter le site
donner envie d’explorer
orienter vers le catalogue
mettre quelques items en avant
rester cohérente avec les autres pages
```

L’expérimentation arrive ici parce que les composants de base sont déjà stabilisés.

---

## Principe

La home peut utiliser des composants plus spécifiques :

```txt
hero
section de mise en avant
appel à l’action
bloc de présentation
liste courte d’items sélectionnés
bloc graphique simple
```

Mais chaque composant doit rester utile.

Un effet visuel qui n’aide pas la compréhension doit être évité.

---

## Composant : hero

Le hero est la première zone forte de la page.

Il peut contenir :

```txt
titre principal
phrase d’introduction
appel vers le catalogue
image ou élément graphique modeste
```

Particularités à comprendre :

```txt
le hero ne remplace pas le contenu
il doit expliquer rapidement le site
il doit rester lisible sur mobile
il ne doit pas repousser tout le contenu utile trop bas
```

Ne créez pas un hero qui prend tout l’écran sans raison.

---

## Composant : appel à l’action

Un appel à l’action doit être clair.

Exemples :

```txt
Explorer le catalogue
Voir les items récents
Rechercher un item
Découvrir le projet
```

Il ne doit pas y avoir dix appels à l’action concurrents.

Le CSS doit hiérarchiser :

```txt
action principale
actions secondaires
liens simples
```

---

## Composant : mise en avant

La home peut afficher quelques items mis en avant.

Réutilisez autant que possible la carte item.

Ne créez pas un second système de cartes incompatible avec le catalogue.

Particularités à comprendre :

```txt
un composant réutilisable limite le chaos
une variation légère est acceptable
une réinvention complète est inutile
```

Par exemple :

```txt
item-card
item-card--featured
```

La variante doit rester proche du composant d’origine.

---

## Expérimentation modeste

Vous pouvez expérimenter avec :

```txt
espacement plus généreux
fond léger sur une section
composition asymétrique simple
typographie de titre plus marquée
image plus expressive
bordure ou ombre discrète
```

Vous ne devez pas expérimenter avec :

```txt
animations envahissantes
position absolute partout
superpositions fragiles
contenu masqué
texte sur image illisible
effets qui cassent le mobile
```

La home peut être plus graphique.

Elle ne doit pas devenir moins utilisable.

---

## Validation de `home.html`

Vérifiez :

```txt
le site est compréhensible en quelques secondes
l’action principale est visible
les liens vers catalogue et recherche sont accessibles
les composants réutilisés restent cohérents
les éléments graphiques ne gênent pas la lecture
la page fonctionne sur mobile
la page ne crée pas de style contradictoire avec le reste du site
```

---

## Erreurs bloquantes

```txt
home décorative mais peu informative
hero trop grand
texte illisible sur image
trop d’appels à l’action concurrents
composants uniques inutiles
cartes différentes du catalogue sans raison
effets qui cassent le mobile
position utilisée pour fabriquer un faux layout
navigation ou footer modifiés seulement sur la home
```

---

# 9. Préserver `item-search.html` et `about.html`

## Objectif

Même si ces pages ne sont pas encore travaillées en détail, elles ne doivent pas être cassées.

Le style commun doit déjà rendre lisibles :

```txt
les formulaires
les fieldset
les labels
les boutons
les listes
les liens
les sections
```

---

## Recherche

Dans `item-search.html`, le formulaire doit rester utilisable.

Le CSS peut améliorer :

```txt
l’espacement entre champs
la lisibilité des fieldset
la visibilité du bouton
la distinction entre formulaire et résultats
```

Mais ne transformez pas encore la recherche en interface avancée.

La recherche dynamique viendra plus tard.

---

## À propos et contact

Dans `about.html`, le contenu doit rester lisible.

Le formulaire de contact doit être utilisable.

Le CSS peut améliorer :

```txt
la largeur du formulaire
l’espacement des champs
la lisibilité de l’adresse ou des liens
le retour visuel du focus
```

Mais le traitement serveur n’existe pas encore.

Ne faites pas semblant que le formulaire fonctionne.

---

## Validation

Vérifiez :

```txt
item-search.html reste lisible
about.html reste lisible
les formulaires ne débordent pas
les labels restent visibles
les fieldset restent compréhensibles
les boutons sont atteignables
le focus reste visible
```

---

## Erreurs bloquantes

```txt
formulaire cassé par le CSS
labels cachés
fieldset invisibles
bouton trop petit
champs trop larges sur mobile
focus invisible
fausse interaction visuelle qui laisse croire que le formulaire est traité
```

---

# 10. Mobile d’abord, desktop ensuite

## Objectif

Le site doit fonctionner sur petit écran avant d’être enrichi sur grand écran.

Le mobile n’est pas une correction finale.

C’est le point de départ.

---

## Méthode

Commencez avec :

```txt
une colonne
texte lisible
espacements simples
images fluides
navigation qui revient à la ligne
cartes empilées
formulaires verticaux
```

Ensuite seulement, ajoutez des adaptations pour écrans plus larges :

```txt
deux colonnes sur la page détail
grille de cartes dans le catalogue
sections plus aérées sur la home
navigation plus horizontale
```

---

## Règle

Un breakpoint doit résoudre un problème réel.

N’ajoutez pas des media queries parce que “c’est responsive”.

Ajoutez une media query quand :

```txt
le texte devient trop large
les cartes peuvent passer en plusieurs colonnes
la navigation a assez de place
la page détail peut mieux répartir image et métadonnées
```

---

## Validation

Testez au minimum :

```txt
petit mobile
mobile large
tablette
desktop
```

Vous pouvez utiliser les outils de développement du navigateur.

Mais vérifiez aussi en redimensionnant librement la fenêtre.

---

## Erreurs bloquantes

```txt
desktop correct mais mobile cassé
mobile correct mais desktop illisible
largeurs fixes
scroll horizontal
texte trop petit
cartes écrasées
navigation qui sort de l’écran
media queries utilisées sans raison
```

---

# 11. Ne pas cacher les problèmes

## Objectif

Le CSS ne doit pas masquer les erreurs.

Ne cachez pas un contenu parce qu’il dérange.

Ne poussez pas un élément hors écran.

Ne forcez pas une hauteur pour éviter de gérer un contenu réel.

---

## Mauvais réflexes

```txt
overflow hidden pour cacher un débordement incompris
height fixe pour contrôler une carte
position absolute pour déplacer un bloc gênant
display none pour masquer un titre ou un label
margin négative pour corriger un alignement
```

Ces corrections créent souvent des problèmes plus graves.

---

## Bon réflexe

Quand un élément gêne, demandez :

```txt
son HTML est-il correct ?
sa place dans le document est-elle logique ?
son contenu est-il trop long ?
son composant est-il mal défini ?
le parent doit-il être en grid, flex ou flux naturel ?
```

Le CSS doit rendre le problème visible et réglable.

Pas le cacher.

---

## Erreurs bloquantes

```txt
contenu important masqué
label caché
titre caché
overflow hidden utilisé pour cacher un bug
marges négatives
position utilisée pour éviter de comprendre le layout
hauteur fixe qui coupe du contenu
```

---

# 12. Organisation du fichier CSS

## Objectif

Le fichier `app.css` doit être lisible.

Il ne doit pas devenir une suite aléatoire de règles.

---

## Ordre conseillé

Organisez le fichier ainsi :

```txt
1. variables
2. base générale
3. layout global
4. header
5. navigation
6. footer
7. composants communs simples
8. item-show
9. item-index
10. home
11. formulaires simples
12. adaptations responsive
```

Vous pouvez adapter l’ordre.

Mais il doit être logique.

---

## Commentaires sobres

Les commentaires peuvent aider.

Exemple :

```css
/* Header */
/* Navigation */
/* Item detail */
/* Catalog grid */
/* Home */
```

N’écrivez pas un commentaire pour chaque ligne.

---

## Éviter la duplication

Si vous écrivez trois fois la même règle, il faut probablement un composant commun.

Exemple :

```txt
même padding
même bordure
même rayon
même style de lien
même style de bouton
```

Regroupez ce qui est réellement commun.

Ne regroupez pas des éléments qui n’ont pas le même rôle.

---

## Validation

Relisez le CSS.

Vous devez pouvoir trouver rapidement :

```txt
les variables
le header
la nav
le footer
la page détail
le catalogue
la home
les formulaires
les règles responsive
```

---

## Erreurs bloquantes

```txt
CSS désordonné
règles dupliquées partout
sélecteurs trop longs
règles mortes
noms de classes incohérents
styles page par page impossibles à réutiliser
commentaires inutiles ou absents sur les grandes sections
```

---

# 13. Tester après chaque composant

## Objectif

Ne stylisez pas tout avant de tester.

Chaque composant doit être vérifié immédiatement.

---

## Ordre de test conseillé

```txt
1. charger le CSS sur toutes les pages
2. tester body, texte, liens, images
3. tester header
4. tester navigation
5. tester footer
6. tester item-show
7. tester item-index
8. tester home
9. tester item-search et about avec le style global
10. tester mobile et desktop
```

---

## Méthode

Après chaque bloc CSS :

```txt
ouvrir la page
tester mobile
tester desktop
tester clavier
vérifier le focus
vérifier les débordements
corriger
committer
```

---

## Commits attendus

Exemples :

```txt
Add shared CSS foundation
Style shared header navigation and footer
Style item detail layout
Style catalog grid and item cards
Style home page components
Validate responsive CSS components
```

---

# Résultat final de l’étape

À la fin de cette étape, vous devez avoir :

```txt
un fichier CSS principal chargé partout
des variables de base
un layout global stable
un header cohérent
une navigation cohérente
un footer cohérent
une page détail lisible
un catalogue en grille responsive
des cartes item réutilisables
une home plus expressive mais modeste
des formulaires encore utilisables
un focus visible
aucun scroll horizontal
une interface lisible sur mobile et desktop
```

Vous êtes alors prêt à passer à l’étape Apache, `.htaccess` et URL locale.

Pas avant.

---

## Checklist finale

```txt
[ ] assets/css/app.css existe.
[ ] Toutes les pages chargent le même fichier CSS.
[ ] Aucun style="" n’est présent.
[ ] Aucune balise <style> n’est présente.

[ ] Les variables de base existent.
[ ] Les couleurs viennent de la direction graphique.
[ ] Le texte est lisible.
[ ] Les liens restent visibles.
[ ] Le focus reste visible.
[ ] Les images ne débordent pas.

[ ] Le layout global est cohérent.
[ ] Le header est cohérent sur toutes les pages.
[ ] La navigation est cohérente sur toutes les pages.
[ ] La navigation fonctionne sur mobile.
[ ] Le footer est cohérent sur toutes les pages.

[ ] Les classes ajoutées nomment des composants.
[ ] Aucun div n’a été ajouté pour décorer.
[ ] Les sélecteurs restent simples.
[ ] Le CSS est organisé par sections.

[ ] item-show.html est lisible sur mobile.
[ ] item-show.html est lisible sur desktop.
[ ] L’image de détail n’est pas déformée.
[ ] Les métadonnées sont lisibles.
[ ] Les tags sont lisibles.
[ ] Le retour catalogue est visible.

[ ] item-index.html affiche une grille responsive.
[ ] Les cartes item sont distinctes.
[ ] Les cartes item sont cohérentes.
[ ] Chaque carte a un lien détail clair.
[ ] Les cartes ne débordent pas.
[ ] Les images des cartes ne sont pas déformées.

[ ] home.html présente clairement le site.
[ ] L’action principale est visible.
[ ] Les composants graphiques restent modestes.
[ ] La home reste cohérente avec le reste du site.

[ ] item-search.html reste utilisable.
[ ] about.html reste utilisable.
[ ] Les formulaires ne sont pas cassés.
[ ] Les labels restent visibles.
[ ] Les fieldset restent compréhensibles.

[ ] Le site fonctionne sur petit mobile.
[ ] Le site fonctionne sur desktop.
[ ] Aucun scroll horizontal n’apparaît.
[ ] Aucun contenu important n’est masqué.
```

---

## Erreurs bloquantes

Vous ne passez pas à l’étape suivante si :

```txt
le CSS n’est pas chargé partout
une page est cassée par le CSS
le site fonctionne seulement sur desktop
le site fonctionne seulement sur mobile
la navigation déborde
le focus est invisible
les liens ne sont plus identifiables
un formulaire devient inutilisable
une image est déformée
le catalogue crée un scroll horizontal
les cartes sont illisibles
la page détail coupe du contenu
la home casse la cohérence graphique
float est utilisé pour le layout
position est utilisé pour fabriquer le layout
des hauteurs fixes coupent du contenu
des marges négatives corrigent artificiellement un problème
des div ont été ajoutés pour décorer
du contenu important est caché
```

---

## À savoir expliquer

Vous devez pouvoir répondre simplement :

```txt
Pourquoi le CSS arrive-t-il après le HTML valide ?
Pourquoi commence-t-on par les éléments communs ?
Pourquoi le flux naturel reste-t-il important ?
Quand utiliser flex ?
Quand utiliser grid ?
Pourquoi ne faut-il pas tout mettre en flex ?
Pourquoi ne faut-il pas tout mettre en grid ?
Pourquoi évite-t-on float pour le layout moderne ?
Pourquoi évite-t-on position pour fabriquer une mise en page ?
Pourquoi la page détail est-elle travaillée avant le catalogue ?
Pourquoi le catalogue utilise-t-il souvent une grille ?
Qu’est-ce qu’une carte item réutilisable ?
Pourquoi la home peut-elle expérimenter seulement après les composants communs ?
Pourquoi le mobile doit-il fonctionner avant le desktop ?
Pourquoi ne faut-il pas cacher un problème avec overflow hidden ?
Pourquoi le focus visible reste-t-il obligatoire ?
Comment vérifier qu’un composant est réutilisable ?
```

---

## Phrase à retenir

Le CSS ne crée pas la structure.

Il agence proprement la structure qui existe déjà.
