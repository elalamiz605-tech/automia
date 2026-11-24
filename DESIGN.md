# DESIGN.md — Site de l'agence

Direction : **« atelier technique, chaleureux »**. Une agence qui parle à des
commerçants et des PME, pas à des développeurs. Sérieux et précis (on touche à
leurs outils, leurs clients, leur argent), mais accessible et humain.
Fond clair légèrement teinté de vert, encre presque noire, un seul vert profond pour l'action,
un ambre chaud pour les détails. Pas de dégradé violet, pas de verre dépoli,
pas d'emoji comme icônes.

> Direction choisie sans bibliothèque de références connectée (UXKIN non
> connecté) : basée sur la cible, l'objectif (demandes de devis) et les règles
> ci-dessous.

## Couleurs

| Token | Clair | Sombre | Rôle |
|---|---|---|---|
| `--bg` | `#F5F7F4` | `#0D1110` | Fond de page |
| `--surface` | `#FFFFFF` | `#151B18` | Cartes, formulaire, schéma du hero |
| `--surface-2` | `#EAF0EB` | `#1B2320` | Sections alternées, puces |
| `--border` | `#D6DED8` | `#2A3430` | Bordures, séparateurs |
| `--text` | `#121614` | `#EAF0EC` | Texte principal, titres |
| `--text-muted` | `#535C57` | `#A2ADA7` | Texte secondaire (≥ 4.5:1) |
| `--primary` | `#0F6B4F` | `#3FCF98` | Boutons principaux, liens, focus |
| `--primary-hover` | `#0B563F` | `#5EDCAB` | Survol du primaire |
| `--on-primary` | `#FFFFFF` | `#0B1A14` | Texte sur le primaire |
| `--primary-soft` | `#E3F1EA` | `#17302A` | Fonds d'icônes, badges |
| `--accent` | `#E9A23B` | `#F2B85C` | Détails seulement (points, soulignés). Jamais pour du texte sur fond clair |
| `--success` | `#1E7F4F` | `#4CC98A` | Message envoyé |
| `--error` | `#B3261E` | `#F2847C` | Erreurs de formulaire |

Contraste vérifié : `--text` / `--bg` ≈ 17:1, `--text-muted` / `--bg` ≈ 6.3:1,
blanc / `--primary` ≈ 6.6:1.

## Typographie

- Titres : **Bricolage Grotesque** (600–700), un peu de caractère, lisible.
- Texte : **Instrument Sans** (400, 500, 600).
- Journal d'exécution : **JetBrains Mono**.
- Taille de base 17px, interligne 1.6, lignes de 60 à 72 caractères max.

| Token | Taille | Interligne | Usage |
|---|---|---|---|
| `--fs-xs` | 0.8125rem | 1.4 | Étiquettes, mentions |
| `--fs-sm` | 0.9375rem | 1.5 | Texte secondaire |
| `--fs-base` | 1.0625rem | 1.6 | Paragraphes |
| `--fs-lg` | 1.25rem | 1.5 | Chapeaux, intros |
| `--fs-xl` | 1.625rem | 1.25 | Titres de carte (h3) |
| `--fs-2xl` | clamp(2rem, 4vw, 2.75rem) | 1.1 | Titres de section (h2) |
| `--fs-3xl` | clamp(2.5rem, 6vw, 4.25rem) | 1.02 | Titre du hero (h1) |

## Espacement

Échelle de 8 px : `--s-1` 4, `--s-2` 8, `--s-3` 12, `--s-4` 16, `--s-5` 24,
`--s-6` 32, `--s-7` 48, `--s-8` 64, `--s-9` 96, `--s-10` 128.
Sections : `--s-9` en haut et en bas (`--s-8` sur mobile).
Largeur de contenu : 1160px, marges latérales 20px sur mobile, 32px au-delà.

## Forme et profondeur

- Rayons : `--r-sm` 6px (puces, champs), `--r-md` 12px (boutons, cartes),
  `--r-lg` 20px (grands blocs).
- Une seule ombre : `--shadow` pour le schéma du hero et le formulaire.
  Le reste est délimité par des bordures.

## Composants

- **Bouton principal** : fond `--primary`, texte `--on-primary`, 48px de haut,
  `--r-md`. Survol `--primary-hover`. Focus : anneau 3px `--primary` décalé
  de 3px. Désactivé : opacité 0.5.
- **Bouton secondaire** : fond transparent, bordure `--border`, texte `--text`.
  Survol : fond `--surface-2`.
- **Bouton discret** : texte `--primary` souligné au survol.
- **Liens** : `--primary`, soulignés dans le texte courant.
- **Champs** : fond `--surface`, bordure `--border`, 48px, `--r-sm`, focus
  bordure `--primary` + anneau. Libellé toujours visible au-dessus.
- **Cartes** : `--surface`, bordure `--border`, `--r-md`, sans ombre.
- **Navigation** : collante, fond `--bg` à 92 % d'opacité, bordure basse au
  défilement. Menu repliable sur mobile.
- **Pied de page** : `--surface-2`, liens en `--text-muted`.

## Mouvement

- Fond animé en 3 couches fixes, derrière le contenu :
  1. halos de lumière (vert `--primary`, ambre `--accent`) qui dérivent lentement ;
  2. grille de points fine, visible surtout en haut de page ;
  3. réseau de nœuds (canvas) : des « hubs » verts déclenchent des ondes et
     envoient des impulsions avec traînée qui circulent de nœud en nœud,
     effet de profondeur au défilement, et liens vers le curseur de la souris.
  En pause quand l'onglet est caché, figé si `prefers-reduced-motion`.
- Schéma du hero : les 4 étapes s'allument l'une après l'autre en boucle.
- Démo d'automatisation (section `#demo`), style éditeur n8n/Make : nœuds reliés par
  des courbes, paquet de données qui circule, badge « en cours » puis ✓, aiguilleur
  (router) qui grise les chemins non pris, journal d'exécution en police mono.
  3 cas (réservation, question, devis) en boucle, ou au clic. Ne tourne que si
  la section est visible ; version figée si `prefers-reduced-motion`.
- Calculateur : les chiffres défilent jusqu'à la nouvelle valeur.

## Images et icônes

- Icônes : **Lucide** (trait 1.75), en SVG intégré, couleur `--primary` sur
  fond `--primary-soft`.
- Pas de photos de banque d'images. Le visuel principal est un **schéma
  d'automatisation** dessiné en HTML/CSS (étapes reliées) qui montre le
  service concrètement.
- Plus tard : vraies captures des projets clients, une fois qu'il y en a.
