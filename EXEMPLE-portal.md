<!-- ============================================================================
     EXEMPLE — page PORTAIL en grammaire v2 (directives @).
     Voir CLAUDE.md pour la référence complète du format.

     Le portail réutilise le même modèle @section/@palette, mais son rendu est
     bespoke (grille de projets découverte, cartes membres avec réseaux sociaux,
     surfaces éditoriales). Palettes reconnues côté portail :
       @features · @projectlist · @partners · @members · @stats · prose (texte libre)
     Champ de section « - surface: light | mid | ink » → registre éditorial.
     Chrome (hors sections) : @meta / @header / @hero / @contact / @footer.
     ============================================================================ -->

@meta
- primary_color: #1e3a5f
- favicon: data/placeholder.png
- page_bg_color: #eef2f7
- surface_color: #ffffff

@header
- site_name: IAIS
- site_subtitle: Institut d'Analyse Interdisciplinaire des Savoirs
- logo_url: data/placeholder.png

@hero
- title: La recherche au cœur de nos collaborations
- subtitle: Institut d'Analyse Interdisciplinaire des Savoirs
- description: Plateforme centralisant nos projets de recherche.
- cta_label: Découvrir nos projets
- cta_url: #projects
- background: data/placeholder.jpg

@contact
- title: Contactez-nous
- email: contact@exemple.fr
- phone: +33 4 78 78 70 00
- address: 92 rue Pasteur, 69007 Lyon, France

@footer
- copyright: © 2026 IAIS — Tous droits réservés
- social_linkedin: https://linkedin.com/company/iais
- social_github: https://github.com/iais

@section stats "En chiffres"
- surface: light

@stats
@item
- value: 15
- label: Projets actifs
@item
- value: 50+
- label: Chercheurs
@item
- value: 200+
- label: Publications

@section features "Recherche"
- surface: light

@features
- description: Nos axes de recherche interdisciplinaires.
@item Intelligence Artificielle
- icon: psychology
- description: Méthodes d'IA appliquées à la recherche interdisciplinaire.
@item Santé & Bien-être
- icon: favorite
- description: Analyse de données de santé et solutions de suivi.

@section projects "Projets"
- surface: mid

@projectlist
- description: Explorez nos différents domaines de recherche.

@section partners "Partenaires"
- surface: light

@partners
@item Partenaire externe
- logo: data/placeholder.jpg
- url: https://exemple.fr
- description: Description du partenaire (lien externe).
@item Projet interne
- logo: data/placeholder.jpg
- url: /project/exemple
- description: Lien interne vers une page projet.

@section members "Membres"
- surface: mid

@members
@item Prénom Nom
- image: data/placeholder.jpg
- description: Rôle et rattachement.
- email: prenom.nom@exemple.fr
- linkedin: https://linkedin.com/in/prenom-nom

@section about "À propos"
- surface: ink

Présentation de l'institut : sa mission, favoriser la collaboration et rendre
la recherche [ouverte et accessible](https://exemple.fr). Ce texte libre (prose)
devient un bloc de type « text ».
