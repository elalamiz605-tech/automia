# Automia — site web

Site vitrine d'**Automia**, agence d'automatisation et d'IA en Espagne
(espagnol / français). Un seul fichier `index.html`, sans dépendances ni étape
de build : il s'ouvre directement dans un navigateur.

## Ce que contient la page

- Haut de page avec démo animée (WhatsApp → IA → agenda → rappel)
- Démo d'automatisation style n8n / Make (réservation, question, devis)
- Réceptionniste IA 24/7 multilingue (produit phare)
- Services : automatiser, être trouvé, attirer des clients
- Packs par secteur, formules Despega / Crece / Domina
- Calculateur « combien tu perds », méthode, FAQ, formulaire WhatsApp
- Fond animé, mode clair / sombre, ES / FR

## À compléter avant la mise en ligne

1. **Contact** : en bas de `index.html`, dans `CONFIG`, remplacer le numéro
   WhatsApp et l'email d'exemple.
2. **Prix** : chercher `PRECIO` dans `index.html`.
3. **Pages légales** (obligatoires en Espagne, LSSI et RGPD) : aviso legal,
   privacidad, cookies. Les liens du pied de page pointent vers `#`.
4. **Avis clients** : un emplacement est prévu (chercher `TESTIMONIALS`).
   N'ajouter que des avis réels.

## Mettre en ligne avec GitHub Pages

Dans le dépôt GitHub : **Settings → Pages → Build and deployment →
Source : Deploy from a branch → Branch : `main` / `(root)` → Save**.
Le site sera disponible quelques minutes plus tard à
`https://<ton-utilisateur>.github.io/<nom-du-depot>/`.

## Style

Les choix de couleurs, typographies et animations sont décrits dans
[`DESIGN.md`](DESIGN.md).
