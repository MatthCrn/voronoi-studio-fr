# Composition de panneaux — version 1.11

## Format global et jeu

Le sélecteur **Motif / Composition** ouvre un espace de composition généraliste.
Dans **Support**, saisir le format global, éventuellement lié à l’une des quinze
proportions d’or. Dans **Panneaux**, régler le nombre souhaité et le **Jeu**.

Le jeu est l’espacement physique entre les panneaux. Il est réservé à chaque
séparation à l’intérieur du format global. Aucun jeu périphérique n’est ajouté.
Les panneaux restent rectangulaires, alignés et sans chevauchement. Les côtés
respectent une dimension minimale réglable, de 20 mm par défaut. Une composition
incompatible avec les contraintes est signalée et ne peut pas être exportée.

## Proposer et manipuler

**Proposer des compositions** affiche jusqu’à trois répartitions différentes pour
1 à 24 panneaux. Une miniature applique la proposition au dessin. Les divisions
utilisent notamment la moitié et des répartitions liées à φ. Chaque disposition
est conservée dans le projet ; les propositions sont reproductibles par graine.

- Glisser un panneau au centre d’un autre : permuter leurs emplacements.
- Le déposer près d’un bord : l’insérer à gauche, à droite, au-dessus ou en dessous.
- Tirer une séparation : modifier les dimensions des zones adjacentes.
- Les séparations s’accrochent aux proportions des quinze rectangles d’or et à
  la moitié. Maintenir Alt pour ajuster librement.
- Maj + clic sélectionne le groupe commun contenant les panneaux concernés.
  Le bouton **Sélectionner le groupe** étend aussi la sélection au groupe parent.
- Glisser un panneau d’un groupe sélectionné déplace le groupe entier. Un double
  clic permet de revenir à la sélection individuelle.
- Échap annule le déplacement en cours. Annuler/Rétablir restaure une manipulation
  complète. Les flèches du clavier déplacent une séparation lorsqu’elle a le focus.

La prévisualisation pendant le glissement montre la réorganisation. Un emplacement
incompatible est signalé en rouge et n’est pas appliqué au relâchement. Une zone
vide permet de déplacer la vue ; la molette et les boutons règlent le zoom.

## Sélection et verrouillages

Cliquer sur un panneau dans la vue ou dans la liste de droite. Ses dimensions,
position et proportion apparaissent dans Panneaux. La saisie exacte d’une dimension
ajuste une séparation disponible ; une dimension imposée par le format global
reste désactivée.

**Verrouiller la sélection** conserve les positions et dimensions de ses panneaux.
Les nouvelles propositions régénèrent les zones libres en conservant les limites
nécessaires aux verrouillages. Le changement du nombre de panneaux, du format
global ou du jeu nécessite de déverrouiller les panneaux. Les déplacements qui
modifient indirectement un panneau verrouillé sont refusés.

## Habillage et contours

**Appliquer le motif Voronoi** habille la sélection. Les autres panneaux restent
pleins. Le motif global est échantillonné à la position de chaque panneau ; chaque
panneau possède sa propre bordure. Les contours d’ajours sont réellement reconstruits
dans ces limites, avec les mêmes arrondis organiques et variations spatiales que
le moteur existant. Déplacer un panneau peut donc modifier son échantillon du motif.

**Couleurs des lignes** règle séparément les contours des panneaux et les lignes
intérieures. Les contours sont bleus par défaut, visibles même sur un panneau plein.
La sélection et la cible de glissement ajoutent un repère temporaire à l’écran.

Le SVG reprend les couleurs exactes choisies. Le DXF R12 utilise une palette de
couleurs normalisées, en conservant deux couleurs distinctes. Les fichiers de
panneaux gardent les calques CUT_OUTER / CUT_INNER ; le plan les préfixe par P01_,
P02_, etc. Un contour fermé est présent pour chaque panneau.

## Fichiers

Le projet conserve le format global, les proportions d’or, le jeu, l’arbre de
composition, les identifiants, les verrouillages et l’habillage des panneaux.
Le nouveau format est la version 6 ; les projets versions 1 à 5 restent lisibles,
avec Composition désactivée par défaut.

Dans **Fichier** :

- Plan SVG : vue d’ensemble avec identifiants et dimensions en millimètres.
- Plan DXF : contours et motifs à leurs positions réelles, sur des calques par panneau.
- PNG : image du plan ; les limites de taille du moteur PNG sont conservées.
- Tableau CSV : dimensions, positions, jeu, habillage et verrouillages, en millimètres.
- SVG/DXF du panneau sélectionné : origine locale et dimensions réelles.
- ZIP : plan SVG/DXF, tableau CSV, projet et fichiers SVG laser/DXF de chaque panneau.

Les fichiers laser individuels comprennent le contour fermé et les tracés intérieurs
activés, sans les étiquettes, points générateurs ou Delaunay. Le plan SVG est un
document de repérage coté ; ses annotations ne sont pas destinées à la découpe.
Avec un jeu nul, les contours de panneaux adjacents se superposent sur le plan :
utiliser les fichiers individuels ou contrôler les lignes communes avant usinage.

Les imports SVG restent disponibles dans le mode Motif. Le format global d’une
composition est rectangulaire. La composition n’effectue pas de calcul structurel,
d’assemblage ni d’imbrication sur une plaque de matière première.

## Validation

Tests de géométrie, non-chevauchement, jeu, génération bornée et reproductible,
verrouillages, déplacement, insertion, groupe, cotes, repères d’or, projets,
contours, couleurs, SVG/DXF/CSV et ZIP. Contrôle visuel et manipulation réelle à
la souris : permutation, insertion, séparation, groupe et Annuler/Rétablir.
L’exemple ZIP de six panneaux a été ouvert et ses SVG analysés comme XML.

Le mécanisme de mise à jour Windows est conservé, sans hébergement configuré.
Cette livraison n’actualise pas le site déjà publié et n’installe pas l’application
à la place de la version existante de l’utilisateur.

## Motif continu et visibilité

Un seul motif couvre le format global. Il est découpé selon la position de chaque panneau et les jeux, sans répétition. Les nouveaux panneaux portent le motif par défaut. Un panneau peut rester plein en désactivant **Appliquer le motif Voronoi** sur sa sélection. Les projets existants conservent leurs choix ; **Appliquer le motif à tous les panneaux** permet de les habiller ensemble.

**Afficher le motif** masque uniquement les tracés intérieurs dans la vue de composition. Les contours restent visibles. Les exports PNG, SVG et DXF conservent les motifs appliqués et les contours de panneaux. Les DXF séparent les calques CUT_INNER et CUT_OUTER par panneau. Les repères de points et Delaunay sont exclus des exports de composition.

## Diviser un panneau

Clic droit sur un panneau, puis **Diviser en n…**. Saisir le nombre et choisir **Côte à côte (colonnes)** ou **Superposés (lignes)**. Le dialogue affiche les dimensions résultantes avant validation. Les panneaux créés sont égaux ; les jeux sont déduits des dimensions disponibles. La limite totale est de 24 panneaux, avec une dimension minimale respectée de chaque côté. Un panneau verrouillé ne peut pas être divisé. Les autres panneaux restent à leur place ; le motif est conservé et la division peut être annulée en une étape.

## Sélection multiple et groupes

- Clic simple : sélectionner un panneau, ou son groupe enregistré.
- **Ctrl + clic** (Cmd sur Mac) : ajouter ou retirer un panneau de la sélection.
- **Maj + clic** : sélectionner le groupe enregistré, ou l’ensemble de divisions contenant les panneaux choisis.
- Double-clic : sélectionner un panneau individuel dans un groupe.
- Clic droit : menu des actions sur la sélection. Le clic droit sur un panneau déjà sélectionné conserve toute la sélection.

**Grouper** enregistre l’appartenance des panneaux sans changer leurs positions, dimensions, contours ni jeux. **Dégrouper** sépare les membres sélectionnés du groupe. Le groupe se sélectionne et se verrouille ensemble. Les groupes contigus se déplacent comme un ensemble dans la composition ; leurs dimensions s’adaptent à l’emplacement de destination. Un groupe dispersé peut être déplacé rigidement vers un ensemble d’emplacements de mêmes dimensions et de même disposition. Une cible incompatible est signalée et le déplacement est annulé.

## Fusionner et supprimer

**Fusionner en un panneau** requiert au moins deux panneaux non verrouillés qui composent un rectangle complet, sans panneau manquant ni emplacement vide. Les séparations et les jeux intérieurs disparaissent ; l’étendue extérieure et les autres panneaux sont conservés. Le nouveau panneau reprend le premier identifiant dans l’ordre du plan et porte le motif continu si au moins un panneau sélectionné le portait. La commande explique son indisponibilité si la géométrie ou les verrouillages empêchent de conserver les voisins et leurs jeux.

**Supprimer et laisser vide** retire les panneaux sélectionnés sans agrandir ni déplacer leurs voisins. L’emplacement est représenté en pointillés et n’est présent dans aucun export PNG/SVG/DXF/CSV ni dans les fichiers de panneaux. Le clic droit sur la zone propose **Créer un panneau ici**, aux dimensions conservées, avec le motif appliqué. Cette création respecte les 24 panneaux maximum et la dimension minimale. Une nouvelle proposition peut réorganiser les zones non verrouillées.

Les opérations s’annulent en une étape, avec leurs groupes et leurs compteurs. Les groupes et les zones vides sont sauvegardés dans les projets au format 7 ; ce format demande la version 1.11 ou ultérieure. La redistribution automatique de la place libérée n’est pas incluse.
