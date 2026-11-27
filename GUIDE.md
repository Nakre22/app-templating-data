# Guide de rédaction — portail et pages projet

Ce guide explique comment écrire le contenu du site en Markdown : créer un projet,
modifier le portail, et ce que fait chaque palette. Les fichiers `EXEMPLE-portal.md`
et `EXEMPLE-projet/` du dépôt de données sont des modèles prêts à copier.

---

## 1. Principe

- **Un dossier = une page.** Le dossier `portal/` produit la page d'accueil ; chaque
  autre dossier produit une page projet, publiée à l'adresse `/project/<nom-du-dossier>`.
- **Publier = pousser sur GitHub.** Le serveur relit le dépôt de données toutes les
  5 minutes. Un push sur la branche suivie est en ligne au plus 5 minutes plus tard.
- **Le Markdown décrit toute la page** grâce à des directives qui commencent par `@`.
- Ignorés par la synchronisation : les dossiers `data/` et `yaml/` à la racine, les
  dossiers dont le nom commence par `EXEMPLE`, et les fichiers `.md` à la racine
  (comme ce guide).

## 2. Organisation du dépôt de données

```
dépôt/
├── data/                  images partagées (branding du portail)
├── portal/
│   └── portal.md          → la page d'accueil
├── mon-projet/            → la page /project/mon-projet
│   ├── index.md           fichier principal
│   ├── membres.md         fichier inclus (facultatif)
│   └── data/              images et fichiers du projet (facultatif)
└── yaml/                  généré par le serveur : ne pas modifier
```

- **Fichier principal** d'un dossier : `index.md`, sinon `<nom-du-dossier>.md`, sinon
  le premier `.md` trouvé.
- **Découper une page** : `@include membres.md` sur sa propre ligne insère un fichier
  du même dossier à cet endroit. Un fichier inclus peut en inclure d'autres.
- **Nom du dossier** : il devient l'adresse de la page. Préférez des minuscules et des
  tirets (`mon-projet`), sans espace ni accent.

## 3. La grammaire en un coup d'œil

| Syntaxe | Rôle |
|---|---|
| `@meta`, `@header`, `@hero`, `@contact`, `@footer` | Réglages de page (couleurs, en-tête, contact…), suivis de lignes `- clé: valeur` |
| `@section <id> "Libellé"` | Ouvre une section. `id` = ancre dans l'adresse (`#id`), le libellé est le titre affiché |
| `- group: Nom` (juste sous `@section`) | Groupe de la section dans le menu latéral (page projet) |
| `- surface: light \| mid \| ink` (juste sous `@section`) | Fond de la section (portail) |
| `@<palette>` (ex. `@people`) | Insère un bloc mis en forme : une liste de membres, de documents… |
| `@item <Nom>` | Ajoute une entrée à la palette, suivie de ses `- clé: valeur` |
| `@end` | Ferme la palette : le texte suivant redevient du texte normal |
| `:::` … `:::` | Bloc de texte libre, utilisable partout, même entre deux items |
| `#` à `######` suivis d'un espace | Vrais titres (H1 à H6) |
| Texte normal | Paragraphes, listes `- x` ou `1. x` |

Exemple complet d'une section :

```markdown
@section equipe "Notre équipe"
- group: Members

## Qui sommes-nous ?
Un paragraphe de présentation avec un [lien](https://exemple.fr).

@people
- description: Introduction affichée au-dessus des fiches.
@item Alice Martin
- role: Chercheuse
- email: alice@exemple.fr
- image: data/alice.jpg
@item Bob Durand
- role: Ingénieur
@end

Texte normal après la liste des membres.
```

### Règles à connaître

- **Libellé de section** : guillemets droits `"…"`, typographiques `“…”`, français `« … »`
  ou aucun guillemet. Sans libellé, l'`id` est affiché.
- **Deux sections avec le même `id`** : la seconde devient `id-2`.
- **Une valeur sur plusieurs lignes** : une ligne qui suit directement `- clé: valeur`
  la prolonge.
- **Après une ligne vide**, seuls les champs de texte (`description`, `abstract`, `bio`,
  `why`, `what`, `how`) continuent, en ajoutant un paragraphe. Un texte placé après un
  lien ou une image n'y est jamais collé :
  - en tête de palette, il devient l'introduction (`description`) ;
  - dans un item, il est ignoré : fermez la palette par `@end` pour écrire du texte après.
- **Texte juste sous `@item`**, avant toute clé : il devient la description de l'item.
- **Nom d'un item** : texte brut. Le gras ou un lien y sont réduits à leur texte.
- **Une palette se ferme seule** au titre `#`, à la palette ou à la section suivante.
  `@end` n'est utile que pour écrire du texte normal juste après.

## 4. Texte riche

Valable dans le texte normal, les blocs `:::` et les champs de texte (`description`,
`abstract`, `bio`, `why`/`what`/`how`).

| Syntaxe | Résultat |
|---|---|
| `**gras**`, `*italique*` | **gras**, *italique* |
| `[texte](https://url)` | Lien, ouvert dans un nouvel onglet |
| `[texte](https://url "Info-bulle")` | Lien avec info-bulle |
| `[texte](#id-de-section)` | Lien vers une section de la même page (même onglet) |
| `![description](data/image.png)` | Image dans le texte |
| `![description](data/image.png){right}` | Image flottante à droite (`left`, `center` aussi) |
| `<img src="data/image.png" align="right" width="180">` | Image flottante, largeur maximale 180 px |
| `- élément` ou `1. élément` (dans le texte normal) | Liste à puces ou numérotée |
| Ligne vide dans un `:::` | Nouveau paragraphe |

## 5. Créer une page projet

1. Créez un dossier au nom de la page, par exemple `mon-projet/`.
2. Copiez-y le contenu de `EXEMPLE-projet/` (ou partez de l'exemple minimal ci-dessous).
3. Mettez les images dans `mon-projet/data/` et écrivez `data/nom.png` dans le Markdown.
4. Poussez sur GitHub. La page apparaît sur `/project/mon-projet` et dans la liste des
   projets du portail.

Exemple minimal :

```markdown
@meta
- project_id: mon-projet
- primary_color: #1850c0

@header
- title: MON PROJET
- subtitle: Une phrase de présentation
- logo: data/logo.png

@contact
- email: contact@exemple.fr

@section home "Accueil"
- group: Home

@whyWhatHow
**why:** Pourquoi ce projet existe.
**what:** Ce qu'il fait.
**how:** Comment il le fait.

@section documents "Publications"
- group: Productions

@documents
@item Titre de l'article
- type: Journal Paper
- author: A. Auteur
- link: https://hal.science/...
```

Mettez `- project_id:` dans `@meta`, avec le nom du dossier : il marque la page comme
un projet dans les données générées. L'adresse de la page vient, elle, du nom du dossier.

### Réglages d'une page projet

**`@meta`** — identité et apparence

| Clé | Effet |
|---|---|
| `project_id` | Identifiant du projet (le nom du dossier) |
| `external_url` | Sur le portail, le projet renvoie vers ce site externe au lieu de sa page |
| `favicon` | Icône de l'onglet (`data/icone.png`) |
| `primary_color` | Couleur principale : liens, accents (`#1850c0`) |
| `secondary_color` | Couleur d'accent secondaire |
| `heading_font` | Police des titres : `playfair` (serif), `source-sans` ou `roboto` |
| `card_style` | Cartes : `elevated` (ombre), `flat` (sans ombre) ou `bordered` (filet) |
| `page_bg_color`, `page_bg_image` | Fond de la page |
| `surface_color`, `text_color`, `divider_color` | Fond des cartes, couleur du texte, couleur des séparateurs |
| `ink_bg`, `ink_fg` | Barre du haut et menu latéral en couleurs sombres (fond, texte) |

**`@header`** — `title` (nom du projet), `subtitle`, `logo`, `category`, `tags`
(séparés par `;`). Le portail reprend `title`, `subtitle` et `tags` dans sa liste.

**`@hero`** — bandeau sous le titre : `description`, `image_url`.

**`@contact`** — `title`, `email`, `phone`, `address`, affichés en bas du menu latéral.

**`@footer`** — `copyright` et liens sociaux (voir le portail).

**Menu latéral** — chaque section y figure sous son `- group:`. Les groupes apparaissent
dans l'ordre où ils sont rencontrés ; leurs noms sont libres (ex. Home, Productions,
News & Events, Miscellaneous, Members).

## 6. Palettes des pages projet

Chaque palette accepte, avant son premier `@item` :
- `- description:` (ou du texte libre) : une introduction en texte riche ;
- `- image:` : une illustration au-dessus de la liste.

Chaque item accepte `- description:` (texte riche). Un bloc `:::` peut s'intercaler
entre deux items.

### `@whyWhatHow` — présentation du projet
Trois blocs Why / What / How, un logo et une bande de logos partenaires.

```markdown
@whyWhatHow
<img src="data/logo.png" align="right" width="180">
**why:** Pourquoi.
**what:** Quoi.
**how:** Comment.
- partner_logo: data/partenaire1.png
- partner_logo: Omundu | data/omundu.png | https://www.omundu.ai/
```
`partner_logo` est répétable : chemin seul, ou `Nom | image | lien` pour un logo cliquable.

### `@people`, `@members`, `@engineers`, `@interns`, `@visitors` — personnes
Fiches avec photo. Champs : `role` (un `;` passe à la ligne), `email`, `phone`, `image`,
`description`, `website`, `website_2`, `website_3`, `website_icon`, `website_2_icon`,
`website_3_icon` (nom d'icône Material, ex. `school`), `linkedin`, `github`, `twitter`,
`instagram`, `youtube`, `facebook`.
Les sites web s'affichent sous leur nom de domaine. Dès qu'un lien a une icône, les
autres reçoivent l'icône `language`.

### `@documents` — publications et documents
Champs : `type`, `author`, `venue`, `abstract` (résumé repliable), `link`.
Le `type` choisit l'icône et la couleur s'il contient `journal`, `conference`,
`technical` ou `research`.

### `@events`, `@seminars` — événements
Classés en trois groupes : à venir, « date à annoncer », passés.
Champs : `date` (`2026-03-20` ou `20/03/2026`), `type` (sa couleur dépend des mots
`demo`, `conf`, `international`, `sem`), `venue`, `author`, `abstract`,
`slides_type` + `slides_value` :
- `slides_type: link` et `slides_value: https://…` → lien vers les diapositives ;
- `slides_type: copy` et `slides_value: email@…` → « diapositives sur demande ».

Une date absente ou illisible place l'événement sous « Date to be announced ».

### `@software` — logiciels
Champs : `author`, `abstract`, `download` (lien de téléchargement ou d'accès).

### `@demos` — vidéos
Champs : `author`, `abstract`, `link`. Le lien peut être :
- une vidéo YouTube (`watch?v=`, `youtu.be`, `shorts`) ou Vimeo → lecteur intégré ;
- un fichier vidéo du dépôt (`data/demo.mp4`, `.webm`, `.mov`…) → lecteur intégré ;
- autre chose → un lien « Watch the video ».

### `@openpositions` — offres de poste
Champs : `date` (publication), `start`, `duration`, `description`, `download` (fiche de poste).

### `@blogs` — blogs et actualités
Champs : `link`, `description`. Sans `link`, le titre s'affiche sans lien.

### `@relatedprojects` — projets liés
Champs : `link`, `description`.

### Palettes simples
Rendues directement dans la section.

| Palette | Champs d'un item | Rendu |
|---|---|---|
| `@tracks` (ou `@projecttracks`) | `description` | Axes de travail numérotés |
| `@stats` | `value`, `label` (avec `@item` seul) | Chiffres clés |
| `@features` | `description` | Grille de cartes |
| `@partners` | `logo`, `url`, `description` | Cartes partenaires cliquables |
| `@team` | `role`, `bio`, `email`, `image` | Cartes d'équipe |
| `@timeline` | `date`, `event` | Frise chronologique |
| `@publications` | `item`, `item_metadata` | Liste simple |
| `@gallery` | `image`, `caption` | Galerie d'images |
| `@links` | `label`, `url` | Liste de liens |
| `@contact` | (champs du bloc) `email`, `phone`, `address` | Coordonnées |

Une palette inconnue est ignorée sans message : vérifiez son orthographe.

## 7. Le portail (page d'accueil)

Le fichier `portal/portal.md` est **obligatoire** : sans lui, le site ne démarre pas.

### Réglages du portail

**`@meta`** — `favicon`, `primary_color`, `secondary_color`, `page_bg_color`,
`page_bg_image`, `surface_color`, `text_color`, et les surfaces :
- `hero_bg`, `hero_fg` : fond et texte du bandeau d'accueil et de la barre de navigation ;
- `ink_bg`, `ink_fg` : fond et texte des sections `ink` et du pied de page.

**`@header`** — `site_name`, `site_subtitle`, `logo_url`.

**`@hero`** — bandeau d'accueil : `title`, `subtitle`, `description`, `cta_label`
(texte du bouton), `cta_url`, `background` (image). Le bouton :
- `#projects` (une ancre) → défile jusqu'à la section ;
- `https://…` → ouvre un nouvel onglet ;
- `/project/x` → change de page.

**`@contact`** — `title`, `email`, `phone`, `address`.

**`@footer`** — `copyright`, `social_website`, `social_linkedin`, `social_github`,
`social_twitter`, `social_instagram`, `social_youtube`, `social_facebook`.

### Sections du portail

Chaque `@section` devient une entrée de la barre de navigation (plus « Contact » si
`@contact` existe). `- surface:` choisit son fond : `light` (défaut), `mid` ou `ink`.

| Palette | Champs | Rendu |
|---|---|---|
| `@stats` | `@item` seul + `value`, `label` | Chiffres clés ; ce qui suit le nombre (`+` dans `200+`) est mis en couleur |
| `@features` | `icon` (nom d'icône Material, ex. `psychology`), `description` | Axes de recherche |
| `@projectlist` | `description` (du bloc) | **Liste automatique de tous les projets** du dépôt |
| `@partners` | `logo`, `url`, `description` | Grille de logos. `url` peut être externe ou `/project/x` |
| `@members` | `image`, `description`, `email`, `phone`, `website`…, réseaux sociaux | Cartes portrait |
| Texte normal, titres | — | Paragraphes, ex. une section « À propos » |

Un projet apparaît dans `@projectlist` dès que son dossier existe. Avec
`- external_url:` dans son `@meta`, il renvoie vers ce site externe.

## 8. Images et fichiers

- Écrivez toujours `data/nom-du-fichier.ext`.
- Si le dossier du projet contient un `data/`, **toutes** ses références `data/…`
  pointent vers ce dossier local. Sinon, elles pointent vers le `data/` partagé de la racine.
- Les PDF, ZIP, vidéos… placés dans `data/` sont téléchargeables avec un simple lien :
  `[Rapport](data/rapport.pdf)`.
- Les images ne sont jamais étirées : une photo large ou un logo gardent leurs proportions.
- Supprimer un fichier de `data/` le supprime du site ; supprimer un dossier projet
  supprime sa page.

## 9. Dépannage

| Symptôme | Cause probable |
|---|---|
| La page n'est pas à jour | Attendre jusqu'à 5 minutes après le push |
| La page affiche « could not be found » | Adresse différente du nom du dossier, dossier sans `.md`, ou fichier sans aucune directive `@section`/`@meta` |
| Une section est fusionnée avec la précédente | `@section` mal écrit : la directive s'écrit en minuscules et seule sur sa ligne |
| Du texte a disparu après une liste | Il suivait un item sans `@end` : ajoutez `@end` avant le texte |
| Un événement est sous « Date to be announced » | Date absente, impossible (31 février) ou dans un autre format |
| Une vidéo s'affiche comme un simple lien | Hébergeur autre que YouTube/Vimeo, ou lien `http` (non `https`) |
| Une image est cassée | Fichier absent de `data/`, ou nom différent (majuscules comprises) |
| Une palette n'apparaît pas | Nom de palette mal orthographié |
| Un lien `#section` ne mène nulle part | L'`id` ne correspond à aucune `@section` de la page |
