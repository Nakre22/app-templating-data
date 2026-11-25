<!-- ============================================================================
     EXEMPLE — page PROJET en grammaire v2 (directives @).
     Voir CLAUDE.md pour la référence complète du format.

     Structure du dossier : une page = un dossier.
       index.md          → ce fichier : singletons (chrome) + la liste des
                           sections, une par ligne, assemblées avant parsing.
       <section>.md      → un fichier par section ; le nom du fichier = l'id
                           de la section (ex. home.md, members.md). Agnostique :
                           renommez/réordonnez librement.
       data/             → sous-dossier local optionnel (images du projet).

     Règles clés :
       @meta / @header / @hero / @contact / @footer  → singletons (chrome de page)
       @section <id> "Libellé libre"                 → une section (ancre = id)
         - group: <Groupe de sidebar>                → champ de section
       @<palette>                                    → un bloc réutilisable
         @item <Nom>                                 → une entrée de liste
       #, ##, ###                                    → VRAIS titres H1/H2/H3
       :::                                           → bloc de texte libre
       data/x.png  → /api/data/x.png (partagé) ou /api/data/<slug>/x.png si le
                     dossier du projet contient un sous-dossier data/ local

     L'assemblage multi-fichiers se fait par des lignes d'inclusion (voir plus
     bas) : chaque ligne pointe une section-sœur, insérée à sa position.
     ============================================================================ -->

@meta
- project_id: exemple
- project_slug: exemple
- primary_color: #1850c0
- heading_font: playfair

@header
- title: PROJET EXEMPLE
- subtitle: Sous-titre du projet
- logo: data/placeholder.png

@contact
- email: contact@exemple.fr

@include home.md
@include projecttracks.md
@include members.md
@include documents.md
@include events.md
@include relatedprojects.md
