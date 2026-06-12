# Brief-tool — Déploiement (mode autonome)

Outil de découverte charte graphique Jouvessence. Un seul fichier : `index.html`. Aucun build, aucune dépendance.

## 1. Configurer le retour des réponses (Formspree)

1. Créer un compte sur https://formspree.io (plan free : 50 envois/mois — largement suffisant)
2. **New Form** → nommer "Brief Jouvessence" → copier l'endpoint (`https://formspree.io/f/xxxxxxxx`)
3. Dans `index.html`, remplacer la constante en tête de `<script>` :
   ```js
   const FORM_ENDPOINT = "https://formspree.io/f/xxxxxxxx";
   ```
4. Tant que `VOTRE_ID` n'est pas remplacé, le bouton "Envoyer" est masqué automatiquement — l'outil reste utilisable (Copier / Télécharger).

Réception : email Formspree avec `nom`, `role` et le `brief` markdown complet.

## 2. Héberger

**Option A — GitHub Pages** (repo public requis en plan free) :
```bash
cd 05-site/brief-tool
git init && git add . && git commit -m "brief tool v1"
gh repo create jouvessence-brief --public --source=. --push
gh api repos/{owner}/jouvessence-brief/pages -X POST -f "source[branch]=main" -f "source[path]=/"
```
URL : `https://<user>.github.io/jouvessence-brief/`

**Option B — Netlify drag-and-drop** (pas de repo) : glisser le dossier sur https://app.netlify.com/drop → URL immédiate.

## 3. Tester puis envoyer

1. Remplir soi-même de bout en bout → vérifier la réception email Formspree
2. Tester sur mobile (le client ouvrira probablement depuis WhatsApp)
3. Envoyer l'URL au client : *"5 minutes, vos goûts, aucun jargon — vos réponses m'arrivent directement."*

## Notes

- Si plusieurs décideurs : chacun remplit séparément → comparer les briefs en atelier.
- Données : transitent par Formspree (tiers). Contenu non sensible (préférences visuelles).
- Garde-fous intégrés : nom requis, ≥1 direction retenue, max 2 retenues, max 3 priorités, ordre de clic = priorité des preuves.
