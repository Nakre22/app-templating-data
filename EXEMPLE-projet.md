<!--
==============================================================================
  FICHIER D'EXEMPLE / RÉFÉRENCE — PAGE PROJET (ou site de laboratoire)
==============================================================================

  ⚠️  CE FICHIER N'EST PAS SYNCHRONISÉ.
  La synchronisation (GithubMarkdownSyncService) n'itère QUE sur les DOSSIERS
  à la racine du repo, et cherche un .md à l'intérieur ({slug}/{slug}.md).
  Un .md posé directement à la racine est donc ignoré : il sert uniquement
  de documentation pour rédiger de vrais fichiers projet.

  Pour créer une VRAIE page projet :
    1. Créer un dossier {slug}/ à la racine (ex. mon-projet/)
    2. Y mettre un fichier {slug}.md (ex. mon-projet/mon-projet.md)
    3. La sync génère project-{slug}.yml, et le portail affiche une carte.

  ⚠️  Les commentaires <!-- --> ne sont PAS supprimés par le parser. Si vous
  copiez ce fichier comme gabarit dans un dossier {slug}/, RETIREZ les blocs
  de commentaires avant de synchroniser, sinon leur texte peut apparaître.

  ⚠️  Tous les  data/xxx  ci-dessous sont des noms GÉNÉRIQUES à remplacer par
  vos propres fichiers (déposés dans le dossier data/ partagé à la racine).

  Règles générales du format :
    - Markdown pur, PAS de front matter YAML. Toutes les sections : ## nom-section
    - Sections "simples" : lignes  - clé: valeur
    - Sections "listes"  : 3 formats au choix (tableau | ### blocs | mixte)
    - Les chemins  data/fichier.ext  sont réécrits en  /api/data/fichier.ext
      (dossier data/ PARTAGÉ à la racine du repo, pas de préfixe projet).
==============================================================================
-->


<!-- ========================================================================
  ## meta  — configuration + design. C'est meta.project_id qui identifie
  ce fichier comme une PAGE PROJET (vs portail).
========================================================================= -->
## meta
- project_id: mon-projet
- project_slug: mon-projet
- status: active
- primary_color: #1850c0
- secondary_color: #0d9488

<!-- Onglet navigateur : chemin data/ vers une image -->
- favicon: data/favicon.png

<!-- ---- Design avancé (tous optionnels) ---------------------------------
     page_bg_color   → fond de page/sections
     page_bg_image   → image de fond
     surface_color   → sidebar + cartes blanches
     text_color      → couleur du texte principal
     secondary_color → accent (dégradé hero, hover des cartes) ; fallback primary
     divider_color   → séparateurs / bordures de carte (défaut #e2e8f0)
     heading_font    → LISTE BLANCHE : playfair (défaut) | source-sans | roboto
                       (toute autre valeur est IGNORÉE, pas d'import arbitraire)
     card_style      → elevated (défaut, ombre) | flat (sans ombre) | bordered (filet 1px)
-->
- page_bg_color: #e8f0fe
- page_bg_image: data/fond.jpg
- surface_color: #f0f6ff
- text_color: #0d1b3e
- divider_color: #c7d9f0
- heading_font: playfair
- card_style: bordered


<!-- ========================================================================
  ## header — titre affiché + logo. header.title sert de label "Home" dans
  la sidebar des pages lab.
========================================================================= -->
## header
- title: MON PROJET
- subtitle: Sous-titre du projet
- logo: data/logo.png


## contact
- email: contact@exemple.fr


<!-- ========================================================================
  ## home — section riche. Démontre TOUT ce qui est possible en texte riche.

  Logo : une balise <img align> AUTONOME (seule sur sa ligne) devient
  home.logo + home.logo_align + home.logo_width (mise en page CSS Grid).
    align="right"  → logo à droite     align="left" → à gauche
    pas d'align    → centré au-dessus   width="N"   → max-width en px
========================================================================= -->
## home

<img src="data/logo.png" align="right" width="180" alt="logo">

<!-- ---- Bande de logos partenaires (optionnelle) -------------------------
     Lignes  - partner_logo:  répétables. Deux syntaxes :
       Simple   : data/x.png                       → chaîne (non cliquable)
       Enrichie : Nom | data/x.png | https://url    → objet {name, logo, url}
       Le "Nom |" peut être vide : | data/x.png | https://url  (url sans tooltip)
-->
- partner_logo: data/logo-partenaire-1.png
- partner_logo: Partenaire Deux | data/logo-partenaire-2.png | https://exemple.fr
- partner_logo: | data/logo-partenaire-3.png | https://exemple.fr

<!-- Champs texte : **key:** value. Chaque champ = une carte (WHY / WHAT / HOW).
     Démontre : liens [texte](url), gras **x**, italique *x*, astérisque isolé
     non converti (5 * 3), image inline avec alignement. -->

**why:** Description du "pourquoi" du projet — voir [ce lien](https://exemple.fr) pour le contexte. Ce texte peut contenir du **gras** important. Un calcul simple : 5 * 3 = 15 (les astérisques isolés ne sont PAS convertis en gras). On peut aussi mettre de l'*italique*.

**what:** Description du "quoi". <img src="data/schema.png" align="right" width="120"> Cette image flotte à droite du paragraphe et le texte l'enrobe automatiquement. On peut aussi écrire une image Markdown alignée : ![diagramme](data/diagramme.png){left}.

**how:** Description du "comment" : la méthode, l'approche employée pour atteindre les objectifs.


<!-- ========================================================================
  ## projecttracks — grille de cartes "axes/pistes de projet".
  Format ### blocs (recommandé pour texte long).
========================================================================= -->
## projecttracks

Project Tracks

### Axe 1 - Titre de l'axe
- description: Description de ce premier axe de recherche du projet.

### Axe 2 - Titre de l'axe
- description: Description du deuxième axe de recherche du projet.


<!-- ========================================================================
  SECTIONS DE LISTE — 3 formats. Toutes les sections ci-dessous sont des
  "list sections" : members, engineers, interns, visitors, partners,
  events, seminars, openpositions, documents, software, demos, blogs,
  relatedprojects, projecttracks…

  Champs de SECTION (avant le 1er item) :
    - description:  intro rich-text au-dessus de la grille (liens, images, gras)
    - image:        illustration au-dessus de la grille
    - (toute autre  - clé: valeur  avant le 1er item devient un champ de section)

  Blocs  :::  … :::  → texte libre inséré à la position EXACTE, autant de fois
  que voulu. Multi-paragraphe (ligne vide → <br><br>), liens et images.

  Champ  - description:  DANS un item ### → bloc rich-text sous l'abstract.
========================================================================= -->


<!-- ---- FORMAT 1 : tableau Markdown ------------------------------------ -->
## engineers

Ingénieurs

- description: Intro de section avec un [lien](https://exemple.fr) et une image ![logo](data/logo.png).
- image: data/illustration.jpg

| name | role | email | image | linkedin |
|------|------|-------|-------|----------|
| Prénom Nom | Ingénieur·e R&D | prenom.nom@exemple.fr | data/photo.jpg | https://linkedin.com/in/exemple |
| Prénom Nom | DevOps | prenom.nom@exemple.fr | data/photo.jpg | https://github.com/exemple |


<!-- ---- FORMAT 2 : ### blocs (préféré pour texte long) ----------------- -->
<!-- Personnes : role, email, phone, description, image + liens sociaux :
     linkedin, github, twitter, instagram, youtube, facebook
     Sites web multiples : website, website_2, website_3
     + website_icon, website_2_icon, website_3_icon (icône Material, défaut language) -->
## members

Members

- description: Description de l'équipe. <img src="data/logo.png" align="right" width="120"> Texte d'introduction au-dessus de la grille des membres.
- image: data/photo-equipe.jpg

:::
Bloc de texte libre inséré ici — par exemple : réunion d'équipe chaque **mardi à 10h**. Inscrivez-vous à la [liste de diffusion](mailto:contact@exemple.fr).
:::

### Prénom Nom
- role: Responsable / Investigateur principal
- email: prenom.nom@exemple.fr
- phone: +33 (0) 0 00 00 00 00
- description: Courte biographie. Peut contenir des [liens](https://exemple.fr) et du **gras**.
- website: https://exemple.fr
- website_2: https://scholar.google.fr/
- website_2_icon: school
- website_3: https://hal.science/
- website_3_icon: article
- linkedin: https://linkedin.com/in/exemple
- github: https://github.com/exemple
- image: data/photo.jpg

### Prénom Nom
- role: Doctorant·e
- email: prenom.nom@exemple.fr
- linkedin: https://linkedin.com/in/exemple
- image: data/photo.jpg


## interns
Interns
- description: Texte d'introduction de la section stagiaires.

### Prénom Nom
- role: Stagiaire Master - Développement Web
- email: prenom.nom@exemple.fr
- github: https://github.com/exemple
- image: data/photo.jpg


## visitors
Visitors

### Prénom Nom
- role: Chercheur·se invité·e
- email: prenom.nom@exemple.fr
- image: data/photo.jpg


<!-- ---- Événements : filtrés par DATE en 2 colonnes (Upcoming / Past) ---
     Les blocs ::: apparaissent AU-DESSUS du split (ils n'ont pas de date). -->
## events

Events & Activities

- description: Texte d'introduction de la section événements.

:::
Bloc de texte libre affiché au-dessus des colonnes À venir / Passés.
:::

### Événement à venir
- date: 2030-03-20
- type: Conference
- venue: Lieu de l'événement
- author: Organisateur
- abstract: Description de l'événement, du programme, des intervenants.

### Événement passé
- date: 2020-11-05
- type: Demo Session
- venue: Lieu de l'événement
- author: Organisateur
- abstract: Description de l'événement passé (colonne Archives).


## seminars
Seminars Agenda
- description: Texte d'introduction de la section séminaires.

### Séminaire à venir
- date: 2030-03-15
- type: Invited
- author: Intervenant·e (Affiliation)
- abstract: Résumé de la présentation du séminaire.
- slides_type: link
- slides_value: data/presentation.pdf

### Séminaire passé
- date: 2020-09-05
- type: Internal
- author: Intervenant·e interne
- abstract: Résumé du séminaire passé.
- slides_type: copy
- slides_value: prenom.nom@exemple.fr


## openpositions
Open Positions
- description: Texte d'introduction des offres. Postes financés, etc.
- image: data/illustration.jpg

### Titre de l'offre (ex. Thèse / Post-doc / Stage)
- date: 2030-12-20
- start: 2031-01-01
- duration: 3 ans
- description: Détail de l'offre, profil recherché. **Candidatures jusqu'au …**
- download: data/offre.pdf

:::
Bloc d'informations communes à toutes les offres (conditions, contact…).
:::

### Deuxième offre
- date: 2030-12-10
- start: 2031-02-01
- duration: 1 an renouvelable
- download: data/offre.pdf


## documents
Documents & Publications
- description: Publications en accès libre. ![logo](data/logo.png){right} Texte d'intro.
- image: data/logo.png

### Titre de la publication
- type: Conference Paper
- author: A. Auteur - B. Auteur
- venue: Nom de la conférence / revue (année)
- abstract: Résumé de la publication.
- description: Note complémentaire avec un [lien vers l'article](https://exemple.fr).
- link: https://exemple.fr

:::
<img src="data/logo.png" align="left" width="64">
Bloc de texte libre inséré entre deux publications.
:::

### Document PDF local
- type: General
- author: Auteur
- venue: Interne (v1.0)
- abstract: Document servi depuis le dossier data/.
- link: data/document.pdf


## software
Software & Tools
- description: Texte d'introduction de la section logiciels.

### Nom du logiciel
- author: Auteur / équipe
- abstract: Description du logiciel, de ses fonctionnalités.
- download: https://exemple.fr

### Archive téléchargeable (ZIP)
- author: Équipe
- abstract: Archive servie depuis data/.
- download: data/archive.zip


## demos
Demos
- description: Un lien data/ est hébergé localement ; un lien externe ouvre un embed YouTube.

### Démo vidéo externe (YouTube)
- author: Auteur
- abstract: Description de la démo.
- link: https://www.youtube.com/embed/VIDEO_ID

### Démo vidéo locale (MP4)
- author: Auteur
- abstract: Fichier vidéo servi depuis data/.
- link: data/video.mp4


## blogs
Blog & News

### Titre du billet
- link: https://exemple.fr
- description: Description du billet de blog (optionnelle).

### Billet sans description
- link: https://exemple.fr


<!-- ---- Partners : cartes avec logo, url, description ------------------ -->
## partners
Partners & Collaborators
- description: Texte d'introduction de la section partenaires.

### Partenaire Un
- logo: data/logo-partenaire-1.png
- url: https://exemple.fr
- description: Description du partenaire.

### Partenaire Deux
- logo: data/logo-partenaire-2.png
- url: https://exemple.fr
- description: Description du partenaire.


## relatedprojects
Related Projects
- description: Projets partageant des objectifs, des données ou des membres.

### Projet lié avec description
- link: https://exemple.fr
- description: Description du projet lié.

### Projet lié sans description
- link: https://exemple.fr


<!--
==============================================================================
  MÉMO ALIGNEMENT D'IMAGES (valable dans TOUT contexte rich-text :
  ## home, ## about, - description:, item - description:, blocs :::)

    <img src="data/img.png" align="right" width="180">   → float right, max 180px
    <img src="data/img.png" align="left">                → float left
    <img src="data/img.png" align="center">              → bloc centré
    ![alt](data/img.png){right}   {left}   {center}      → équivalents Markdown
    ![alt](data/img.png)                                 → inline (pas de float)

  Liens & images inline dans n'importe quel texte :
    [texte](url)        → <a href="url" target="_blank">texte</a>
    ![alt](data/x.png)  → <img src="/api/data/x.png" alt="alt">
==============================================================================
-->
