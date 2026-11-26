@section members "Membres"
- group: Members

@members
- description: Notre équipe pluridisciplinaire. Texte riche avec [liens](https://exemple.fr).

:::
Un bloc `:::` insère du texte libre n'importe où dans la section, y compris
entre deux items.
:::

@item Prénom Nom
- role: Chercheur·e
- email: prenom.nom@exemple.fr
- linkedin: https://linkedin.com/in/prenom-nom
- image: data/placeholder.png

@item Autre Personne
- role: Ingénieur·e
- email: autre@exemple.fr
- website: https://exemple.fr/autre-personne
- website_2: https://scholar.google.fr/
- website_2_icon: school
- image: data/placeholder.png
@end

Texte libre après la palette. Sans « @end », il prolongerait le dernier champ
de l'item précédent (ici l'image).
