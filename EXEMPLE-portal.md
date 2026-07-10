<!--
==============================================================================
  FICHIER D'EXEMPLE / RÉFÉRENCE — PAGE PORTAIL (page d'accueil du site)
==============================================================================

  ⚠️  CE FICHIER N'EST PAS SYNCHRONISÉ (voir explication dans EXEMPLE-projet.md).
  La sync n'itère que sur les DOSSIERS de la racine. Un .md à la racine est ignoré.

  Le VRAI portail vit dans :  portal/portal.md  → génère  portal.yml
  Ce fichier DOIT exister pour que le frontend démarre.

  Différence clé avec une page projet : PAS de  meta.project_id  ici.
  C'est l'absence de project_id + le dossier "portal" qui produit portal.yml.

  Le portail découvre les projets automatiquement : il liste /api/content et
  garde les fichiers  project-*.yml. Chaque page projet devient une carte.
    → meta.external_url dans un projet : le clic ouvre cette URL (nouvel onglet).

  ⚠️  Les commentaires <!-- --> ne sont PAS supprimés par le parser : retirez-les
  si vous copiez ce fichier comme gabarit. Tous les  data/xxx  sont des noms
  GÉNÉRIQUES à remplacer par vos propres fichiers du dossier data/ partagé.
==============================================================================
-->


<!-- ========================================================================
  ## meta — design du portail (mêmes champs que pour un projet, SANS project_id).
========================================================================= -->
## meta
- primary_color: #1e3a5f
- secondary_color: #0d9488
- favicon: data/favicon.png
- page_bg_color: #eef2f7
- surface_color: #ffffff
- text_color: #0d1b3e
- divider_color: #e2e8f0
- heading_font: playfair
- card_style: elevated


<!-- ========================================================================
  ## header — barre du haut : nom du site, sous-titre, logo.
========================================================================= -->
## header
- site_name: MON INSTITUT
- site_subtitle: Sous-titre / baseline de l'institut
- logo_url: data/logo.png


<!-- ========================================================================
  ## hero — bandeau principal. hero.description accepte du rich-text (liens).
========================================================================= -->
## hero
- title: Titre principal du portail
- subtitle: Sous-titre du bandeau
- description: Texte d'accroche. Explorez nos [domaines d'expertise](#projects) et découvrez nos équipes.
- cta_label: Découvrir nos projets
- cta_url: #projects
- background: data/banniere.jpg


<!-- ========================================================================
  ## about — bloc "à propos". about.content accepte du rich-text (liens).
========================================================================= -->
## about
- title: À propos
- content: Présentation de l'institut. Notre mission : favoriser la collaboration et rendre la recherche [ouverte et accessible](https://exemple.fr).
- image: data/illustration.jpg


## contact
- title: Contactez-nous
- email: contact@exemple.fr
- phone: +33 0 00 00 00 00
- address: Adresse postale, Ville, Pays


<!-- ========================================================================
  ## footer — copyright + liens sociaux. Les social_* génèrent les icônes SVG
  de marque enregistrées par l'app (twitter, linkedin, github, instagram,
  youtube, facebook) + un lien "website".
========================================================================= -->
## footer
- copyright: © 2026 MON INSTITUT — Tous droits réservés
- social_website: https://exemple.fr
- social_twitter: https://twitter.com/exemple
- social_linkedin: https://linkedin.com/company/exemple
- social_github: https://github.com/exemple
- social_instagram: https://instagram.com/exemple
- social_youtube: https://youtube.com/@exemple
- social_facebook: https://facebook.com/exemple


<!-- ========================================================================
  ## projects — titre/sous-titre de la grille des projets.
  La grille elle-même est REMPLIE AUTOMATIQUEMENT à partir des project-*.yml
  (pas besoin de lister les projets ici).
========================================================================= -->
## projects
- title: Nos Projets
- subtitle: Explorez nos différents domaines de recherche


<!-- ========================================================================
  ## stats — barre de chiffres clés. FORMAT TABLEAU.
========================================================================= -->
## stats

| value | label |
|-------|-------|
| 15   | Projets actifs |
| 50+  | Chercheurs |
| 12   | Pays partenaires |
| 200+ | Publications |


<!-- ========================================================================
  ## features — axes de recherche. FORMAT ### blocs, avec icône Material.
  (Liste des icônes : https://fonts.google.com/icons)
========================================================================= -->
## features

Nos Axes de Recherche

### Premier axe
- description: Description du premier axe de recherche.
- icon: psychology

### Deuxième axe
- description: Description du deuxième axe de recherche.
- icon: favorite

### Troisième axe
- description: Description du troisième axe de recherche.
- icon: bar_chart


<!-- ========================================================================
  ## partners — bande de partenaires du portail. logo + url + description.
  L'url peut être externe (https://…) OU interne (/project/{slug} ou #).
========================================================================= -->
## partners

Nos Partenaires

### Partenaire externe
- logo: data/logo-partenaire-1.png
- url: https://exemple.fr
- description: Description du partenaire.

### Lien interne vers un projet
- logo: data/logo-partenaire-2.png
- url: /project/mon-projet
- description: Exemple de lien interne vers une page projet du site.


<!-- ========================================================================
  ## members — membres du portail. Mêmes champs sociaux qu'en page projet :
  image, description, phone, email, website(+_2/_3 + _icon),
  linkedin, github, twitter, instagram, youtube, facebook.
========================================================================= -->
## members

Nos Membres

### Prénom Nom
- image: data/photo.jpg
- description: Fonction / rôle de la personne
- phone: +33 0 00 00 00 00
- email: prenom.nom@exemple.fr
- website: https://exemple.fr
- website_2: https://scholar.google.fr/
- website_2_icon: school
- linkedin: https://linkedin.com/in/exemple
- github: https://github.com/exemple

### Prénom Nom
- image: data/photo.jpg
- description: Fonction / rôle de la personne
- email: prenom.nom@exemple.fr
- linkedin: https://linkedin.com/in/exemple


<!--
==============================================================================
  RAPPEL — sections attendues sur le portail (toutes optionnelles sauf le
  minimum pour booter) :
    meta, header, hero, about, contact, footer, projects  → sections simples
    stats, features, partners, members                    → sections de liste
  Les projets s'ajoutent SEULS via les fichiers project-*.yml.
==============================================================================
-->
