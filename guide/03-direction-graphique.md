# DA(A)

## Objectif

Cette étape sert à définir la direction visuelle du projet avant d’écrire le CSS.

Le but n’est pas encore de coder l’interface complète.
Le but est de décider quelle ambiance le site doit transmettre, à quel public il s’adresse, et comment cette direction se traduira ensuite dans les composants CSS.

La direction graphique ne concerne pas seulement les couleurs ou le style.
Elle doit intégrer dès le départ :

```txt
la lisibilité
le contraste
le mode clair
le mode sombre
les états interactifs
le focus clavier
les messages d’erreur
les messages de confirmation
les textes alternatifs
la cohérence mobile / desktop
les exigences WCAG AA
```

L’accessibilité n’est pas une correction de fin de projet.
Elle fait partie du design.

## Position dans la progression

Cette étape arrive après l’identité du projet et avant le HTML statique complet.

Vous devez déjà savoir expliquer :

```txt id="qqckoj"
Mon site s’appelle ...
Il sert à ...
L’utilisateur peut y consulter ...
L’objet principal est ...
Un item représente ...
```

Si ces réponses ne sont pas claires, ne commencez pas la direction graphique.

## À créer dans le projet

Créez un fichier de documentation :

```txt id="px0ncc"
documentation/direction-graphique.md
```

Ce fichier doit contenir les décisions graphiques minimales du projet.

Il ne doit pas être long.
Il doit surtout être clair, utilisable et cohérent avec le type de site.

## Principe central

Tous les choix graphiques doivent être pensés pour respecter une cible WCAG AA.

Cela concerne au minimum :

```txt id="s4ijqe"
contraste du texte
contraste des boutons
contraste des liens
contraste des messages d’erreur
contraste des badges
focus visible
taille lisible du texte
états hover / focus / active / disabled
compréhension sans couleur seule
lisibilité en mode clair
lisibilité en mode sombre
```

Une interface peut avoir une identité forte.
Mais elle doit rester lisible, navigable et compréhensible.

## 1. Ambiance du site

Décrivez l’ambiance générale du projet.

Exemples :

```txt id="lwfdfv"
cinéma sombre
culture institutionnelle
jeu vidéo rétro
cuisine chaleureuse
magazine minimal
boutique claire et moderne
portfolio artistique
catalogue documentaire
site éducatif sobre
```

Votre ambiance doit correspondre au sujet.

Exemples :

```txt id="b0ya7p"
Un catalogue de films d’horreur peut utiliser une ambiance sombre, contrastée et immersive.

Un site de recettes familiales peut utiliser une ambiance claire, chaleureuse et lisible.

Un catalogue d’expositions peut utiliser une ambiance sobre, aérée et éditoriale.
```

Mais l’ambiance ne justifie pas une interface illisible.

Exemples d’erreurs :

```txt id="h1cw4g"
cinéma sombre avec texte gris foncé sur fond noir
jeu vidéo rétro avec texte minuscule et clignotant
magazine minimal avec liens impossibles à distinguer
boutique moderne avec boutons sans contour ni contraste
```

À éviter :

```txt id="lu54b1"
moderne
beau
cool
stylé
propre
```

Ces mots sont trop vagues s’ils ne sont pas expliqués.

## 2. Public cible

Décrivez pour qui le site est conçu.

Exemples :

```txt id="q37tb4"
visiteurs qui cherchent rapidement une information
clients qui comparent des produits
lecteurs qui consultent des articles
parents qui cherchent une activité
joueurs qui parcourent un catalogue
administrateurs qui encodent des contenus
```

Le public cible influence :

```txt id="wpnhtg"
la taille du texte
le contraste
la densité visuelle
la clarté des boutons
la quantité d’informations visibles
la complexité de la navigation
les besoins en aide visuelle
la simplicité des formulaires
```

Un site destiné à une consultation rapide ne se conçoit pas comme un magazine long format.
Un site destiné à un public large doit rester plus lisible et plus explicite.

## 3. Palette claire et palette sombre

Vous devez prévoir une palette claire et une palette sombre.

Le dark mode ne doit pas être improvisé plus tard.
Il doit être pensé dès la direction graphique.

Vous devez choisir :

```txt id="vk5o0k"
fond clair
texte sur fond clair
surface claire
couleur principale claire
couleur secondaire claire
erreur sur fond clair
confirmation sur fond clair

fond sombre
texte sur fond sombre
surface sombre
couleur principale sombre
couleur secondaire sombre
erreur sur fond sombre
confirmation sur fond sombre
```

Exemple :

```txt id="y73qor"
Mode clair
Fond : #ffffff
Surface : #f6f7f9
Texte : #111111
Principale : #3344ff
Secondaire : #e8ecff
Erreur : #b00020
Confirmation : #146c2e

Mode sombre
Fond : #111111
Surface : #1c1c1c
Texte : #f5f5f5
Principale : #9aa7ff
Secondaire : #2b314f
Erreur : #ff8a9a
Confirmation : #7bd88f
```

Ces valeurs sont des exemples.
Chaque projet doit choisir une palette cohérente avec son ambiance.

## 4. Variables CSS prévues

Les couleurs doivent pouvoir être utilisées avec des variables CSS.

Exemple attendu plus tard :

```css id="i0gu5u"
:root {
    --color-bg: #ffffff;
    --color-surface: #f6f7f9;
    --color-text: #111111;
    --color-primary: #3344ff;
    --color-secondary: #e8ecff;
    --color-error: #b00020;
    --color-success: #146c2e;
    --color-focus: #ffbf00;
}

@media (prefers-color-scheme: dark) {
    :root {
        --color-bg: #111111;
        --color-surface: #1c1c1c;
        --color-text: #f5f5f5;
        --color-primary: #9aa7ff;
        --color-secondary: #2b314f;
        --color-error: #ff8a9a;
        --color-success: #7bd88f;
        --color-focus: #ffd166;
    }
}
```

À ce stade, vous ne devez pas encore écrire tout le CSS.
Vous devez préparer les choix qui guideront le CSS.

## 5. Contraste

Votre palette doit permettre de lire correctement le contenu en mode clair et en mode sombre.

Vérifiez au minimum :

```txt id="a1eyv3"
texte principal sur fond
texte secondaire sur fond
lien sur fond
bouton principal
bouton secondaire
bouton danger
message d’erreur
message de confirmation
badge catégorie
badge thème
badge tag
champ de formulaire
focus visible
```

Un texte gris clair sur fond blanc n’est pas acceptable.
Un texte gris foncé sur fond noir n’est pas acceptable.
Un bouton visible en mode clair mais invisible en mode sombre n’est pas acceptable.

La couleur seule ne suffit pas pour transmettre une information.

Exemples :

```txt id="2xg7ac"
Une erreur doit avoir une couleur, mais aussi un texte clair.
Un champ invalide peut avoir une bordure, mais aussi un message.
Un lien doit être reconnaissable autrement que par une légère différence de couleur.
Un bouton désactivé doit rester identifiable comme désactivé.
```

## 6. Typographie

Définissez une typographie simple et lisible.

Vous pouvez choisir :

```txt id="mi6b6g"
une police système
ou une police externe si elle est justifiée
```

Exemples de piles système :

```css id="dw4wp0"
font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
```

ou :

```css id="rmc85z"
font-family: Georgia, "Times New Roman", serif;
```

Vous devez préciser :

```txt id="jqcnrz"
police des titres
police du texte courant
taille de base du texte
hauteur de ligne
graisse des titres
style général : sobre, éditorial, technique, chaleureux, institutionnel...
```

Évitez de multiplier les polices.
Une seule famille bien utilisée suffit souvent.

La typographie doit rester lisible :

```txt id="nz2y22"
sur mobile
sur desktop
en mode clair
en mode sombre
dans les cartes
dans les formulaires
dans les messages d’erreur
```

## 7. Boutons

Décrivez le style des boutons.

Vous devez prévoir au minimum :

```txt id="zfoy2r"
bouton principal
bouton secondaire
bouton danger
état hover
état focus
état active
état disabled
mode clair
mode sombre
```

Exemple de description :

```txt id="zeun72"
Les boutons principaux utilisent la couleur principale, un texte très lisible, un rayon léger et un focus très visible.
Les boutons secondaires sont plus discrets, avec bordure et fond clair ou sombre selon le mode.
Les actions dangereuses utilisent la couleur d’erreur et un libellé explicite.
```

Le bouton doit rester identifiable comme bouton.

À éviter :

```txt id="vysjxk"
bouton uniquement différencié par la couleur
focus supprimé
bouton sans bordure visible en dark mode
bouton danger sans texte clair
bouton désactivé trop pâle pour être compris
```

## 8. Focus clavier

Le focus doit être prévu dans la direction graphique.

Il doit être visible sur :

```txt id="amke8e"
liens
boutons
champs de formulaire
checkbox
radio
select
cartes interactives
pagination
navigation
actions admin
```

Le focus doit fonctionner en mode clair et en mode sombre.

Exemple de règle prévue :

```txt id="u1smy7"
Le focus utilise une couleur dédiée très visible, avec outline ou box-shadow, et ne dépend pas uniquement du changement de couleur du texte.
```

À éviter :

```css id="xa65ej"
outline: none;
```

sans remplacement visible.

## 9. Cartes item

La carte item est un composant central.

Elle servira dans :

```txt id="qfpunf"
la page d’accueil
le catalogue
les résultats de recherche
les collections ou favoris si utilisés
```

Définissez :

```txt id="cjj59u"
forme générale
fond en mode clair
fond en mode sombre
bordure ou ombre
présence ou non d’image
hiérarchie du titre
description courte
affichage de la catégorie
affichage du thème
affichage des tags
lien vers le détail
état hover
état focus si la carte contient un lien principal
```

Exemple :

```txt id="l86pnf"
Les cartes item sont sobres, avec une image en haut, un titre visible, une description courte, puis des badges pour la catégorie et le thème.
Le lien vers le détail est explicite : “Voir le détail”.
En mode sombre, la carte utilise une surface distincte du fond général.
```

À éviter :

```txt id="zry4xv"
carte entièrement cliquable sans lien visible
image sans alt
titre trop petit
tags illisibles
bouton non identifiable
surface sombre indiscernable du fond sombre
```

## 10. Images

Définissez le rôle des images.

Questions à traiter :

```txt id="rzi1y8"
Les images sont-elles informatives ou décoratives ?
Sont-elles centrales dans le projet ?
Ont-elles toutes le même format ?
Faut-il prévoir une image par défaut ?
Comment éviter qu’une image casse la mise en page ?
Comment l’image reste-t-elle lisible en mode sombre ?
```

Exemple :

```txt id="c2j69u"
Les images servent à identifier rapidement un item dans le catalogue.
Elles doivent être recadrées de manière cohérente et accompagnées d’un alt utile.
Si un item n’a pas d’image, une image de remplacement est utilisée.
```

Une image ne doit jamais être nécessaire pour comprendre toute la page.
Le texte doit rester suffisant.

## 11. Formulaires

Les formulaires doivent être pensés avec leurs états.

Vous devez décrire :

```txt id="ej8kpc"
style des labels
style des champs
style des champs au focus
style des champs invalides
style des champs valides si utilisé
style des erreurs
style des messages de confirmation
espacement entre les champs
lisibilité sur mobile
lisibilité en mode clair
lisibilité en mode sombre
```

Exemple :

```txt id="wzjnu7"
Les formulaires sont simples, verticaux, avec labels visibles au-dessus des champs.
Les erreurs apparaissent sous le champ concerné, avec une couleur d’erreur, une bordure visible et un texte explicite.
Le focus est très visible sur chaque champ.
```

Les placeholders ne remplacent pas les labels.

Une erreur ne doit jamais être signalée uniquement par la couleur.

## 12. Messages d’erreur et de confirmation

Prévoyez les styles de retour utilisateur.

Messages à prévoir :

```txt id="fockn9"
erreur générale
erreur de champ
confirmation
avertissement
état vide
404
accès interdit si utilisé
```

Chaque message doit être :

```txt id="znrbdl"
visible
lisible
compréhensible
associé au contexte
utilisable en mode clair
utilisable en mode sombre
non dépendant uniquement de la couleur
```

Exemple :

```txt id="i19yz5"
Un message d’erreur utilise une bordure, une couleur d’erreur, une icône éventuelle non indispensable, et un texte précis.
Un message de confirmation utilise une couleur de succès et indique clairement ce qui vient d’être fait.
```

## 13. Navigation

Décrivez la navigation principale.

Questions :

```txt id="wihx4u"
La navigation est-elle horizontale ou verticale ?
Reste-t-elle simple sur mobile ?
Quels liens sont prioritaires ?
Comment voit-on la page active ?
Comment le focus est-il visible ?
Le lien vers le catalogue est-il visible ?
La navigation fonctionne-t-elle en dark mode ?
```

Exemple :

```txt id="fjqktw"
La navigation principale reste courte : accueil, catalogue, contact.
Sur mobile, elle garde le même ordre et reste utilisable au clavier.
La page active est indiquée visuellement et avec aria-current.
```

Ne créez pas une navigation complexe si le projet n’a que quelques pages.

## 14. Composants à prévoir

Votre direction graphique doit préparer les composants CSS suivants :

```txt id="ocv7sc"
header
navigation
bouton
carte item
formulaire
message d’erreur
message de confirmation
pagination
badge catégorie
badge thème
badge tag
footer
```

Chaque composant doit être pensé pour :

```txt id="r4ygow"
mode clair
mode sombre
focus clavier
contraste WCAG AA
mobile
desktop
états interactifs
```

Vous n’écrivez pas encore toute leur implémentation.
Vous définissez leur intention visuelle.

## 15. Template de documentation à remplir

Copiez cette structure dans :

```txt id="nvcdb2"
documentation/direction-graphique.md
```

Puis complétez-la.

```md id="acpn9w"
# Direction graphique

## Nom du projet

...

## Type de site

...

## Public cible

...

## Ambiance

...

## Objectif accessibilité

Cible : WCAG AA

Principes retenus :
- contraste suffisant en mode clair
- contraste suffisant en mode sombre
- focus clavier visible
- information jamais transmise par la couleur seule
- formulaires lisibles et explicites
- composants utilisables sur mobile et desktop

## Palette — mode clair

| Rôle | Couleur | Justification | Contraste vérifié ? |
|---|---|---|---|
| Fond | ... | ... | oui / non |
| Surface | ... | ... | oui / non |
| Texte | ... | ... | oui / non |
| Principale | ... | ... | oui / non |
| Secondaire | ... | ... | oui / non |
| Erreur | ... | ... | oui / non |
| Confirmation | ... | ... | oui / non |
| Focus | ... | ... | oui / non |

## Palette — mode sombre

| Rôle | Couleur | Justification | Contraste vérifié ? |
|---|---|---|---|
| Fond | ... | ... | oui / non |
| Surface | ... | ... | oui / non |
| Texte | ... | ... | oui / non |
| Principale | ... | ... | oui / non |
| Secondaire | ... | ... | oui / non |
| Erreur | ... | ... | oui / non |
| Confirmation | ... | ... | oui / non |
| Focus | ... | ... | oui / non |

## Typographie

Police des titres :  
Police du texte :  
Taille de base :  
Hauteur de ligne :  
Justification :

## Boutons

Bouton principal :  
Bouton secondaire :  
Bouton danger :  
Hover :  
Focus visible :  
Disabled :  
Dark mode :

## Cartes item

Structure prévue :  
Image :  
Titre :  
Description :  
Catégorie / thème / tags :  
Lien détail :  
Mode clair :  
Mode sombre :  
Focus / hover :

## Images

Rôle des images :  
Format prévu :  
Image par défaut :  
Règle pour les textes alternatifs :  
Comportement en dark mode :

## Formulaires

Labels :  
Champs :  
Focus :  
Champs invalides :  
Messages d’erreur :  
Messages de confirmation :  
Dark mode :

## Navigation

Liens principaux :  
Comportement mobile :  
Page active :  
Focus visible :  
Dark mode :

## Messages

Erreur :  
Confirmation :  
Avertissement :  
État vide :  
404 :

## Composants CSS à créer plus tard

- header
- navigation
- bouton
- carte item
- formulaire
- message d’erreur
- message de confirmation
- pagination
- badge catégorie
- badge thème
- badge tag
- footer
```

## Validation

Cette étape est validée si :

```txt id="ug06lv"
documentation/direction-graphique.md existe
l’ambiance du site est claire
le public cible est identifié
la cible WCAG AA est indiquée
la palette claire est définie
la palette sombre est définie
le contraste a été vérifié pour les deux modes
la typographie est lisible
les boutons sont décrits avec leurs états
le focus clavier est prévu
les cartes item sont décrites
les images sont décrites
les formulaires prévoient erreurs et confirmations
la navigation est décrite
les futurs composants CSS sont listés
chaque composant prévoit mode clair, mode sombre, focus et contraste
```

## Erreurs bloquantes

Vous ne passez pas à l’étape suivante si :

```txt id="kvkbm5"
l’ambiance est vague
le public cible n’est pas défini
les couleurs sont choisies au hasard
le dark mode n’est pas prévu
le contraste est insuffisant
la typographie n’est pas lisible
les boutons ne sont pas identifiables
le focus clavier n’est pas prévu
les cartes item ne sont pas pensées
les images n’ont pas de règle
les formulaires ne prévoient pas d’erreurs visibles
les erreurs dépendent uniquement de la couleur
la navigation n’est pas claire
le CSS commence avant cette documentation
```

## À ne pas faire

Ne commencez pas par écrire :

```css id="yrr7kx"
body {
    background: ...
}
```

sans savoir pourquoi.

Ne choisissez pas dix couleurs.

Ne choisissez pas plusieurs polices décoratives.

Ne copiez pas une charte graphique d’un autre site sans adaptation.

Ne faites pas une interface uniquement jolie sur desktop.

Ne traitez pas le dark mode comme une option ajoutée à la fin.

Ne cachez pas les liens, boutons ou formulaires derrière des effets visuels.

Ne supprimez jamais le focus visible sans le remplacer.

Ne signalez jamais une erreur uniquement par la couleur.

## À savoir expliquer à l’oral

Vous devez pouvoir répondre simplement :

```txt id="hwnxhr"
Quelle ambiance avez-vous choisie ?
Pourquoi cette ambiance correspond-elle au projet ?
Qui est le public cible ?
Quelle est la couleur principale en mode clair ?
Quelle est la couleur principale en mode sombre ?
Comment avez-vous vérifié le contraste ?
Comment les boutons seront-ils reconnaissables ?
Comment le focus clavier sera-t-il visible ?
Comment une carte item sera-t-elle structurée ?
Comment les images seront-elles utilisées ?
Comment les erreurs de formulaire seront-elles visibles ?
Comment la navigation restera-t-elle claire ?
Comment cette direction respecte-t-elle WCAG AA ?
Comment cette direction guidera-t-elle le CSS ?
```

## Phrase à retenir

On ne commence pas le CSS au hasard.

On définit une direction graphique accessible, puis on construit les composants qui servent cette direction.
