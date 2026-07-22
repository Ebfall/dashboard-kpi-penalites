# Tour de contrôle Pénalités — Dashboard KPI

Version prête à héberger sur **GitHub Pages**. Le fichier est un dashboard 100&nbsp;% autonome (HTML + CSS + JS dans un seul fichier) : aucun serveur, aucune base de données — tout tourne dans le navigateur.

## Structure du projet

```
.
└── index.html   ← le dashboard complet (données, logique, mise en forme)
```

## Ce que fait le dashboard

- Suivi des pénalités (brutes, exclusions, taux NUR, pénalités réelles)
- Filtres par site, région, mois, technicien, KPI
- Jauge de la règle "Pénalités si NUR faible"
- Export Excel et PDF
- Chargement d'un classeur Excel (`.xlsx`) via le bouton **"Charger Excel"**, avec **"Actualiser"** qui relit automatiquement le fichier depuis le disque (Chrome/Edge — API File System Access)
- Les saisies KPI par mois sont mémorisées localement dans le navigateur (`localStorage`)

Tout est client-side : il fonctionne à l'identique une fois déployé sur GitHub Pages, sans configuration serveur.

## Déployer sur GitHub Pages (5 minutes)

1. Crée un nouveau dépôt sur GitHub (public), par exemple `dashboard-kpi-penalites`.
2. Publie le contenu de ce dossier :
   ```bash
   git init
   git add .
   git commit -m "Dashboard KPI pénalités"
   git branch -M main
   git remote add origin https://github.com/<ton-compte>/dashboard-kpi-penalites.git
   git push -u origin main
   ```
3. Sur GitHub : **Settings → Pages → Source**, choisis la branche `main` et le dossier `/ (root)`, puis **Save**.
4. Après 1 à 2 minutes, le dashboard est en ligne à l'adresse :
   `https://<ton-compte>.github.io/dashboard-kpi-penalites/`

## Alternative sans ligne de commande

Sur GitHub : **"Add file → Upload files"**, glisse `index.html`, commit, puis active Pages comme à l'étape 3.

## Notes

- Le dashboard embarque déjà les données (bloc `<script id="DATA" type="application/json">`) — pas de fichier externe à copier à part `index.html`.
- Les librairies Chart.js et SheetJS sont chargées depuis un CDN (`cdnjs.cloudflare.com`) : une connexion internet est nécessaire pour l'affichage des graphiques et l'export Excel, ce qui est le cas normal une fois le site hébergé.
- Si tu remplaces les données ou le classeur source, tu peux soit régénérer le bloc `DATA`, soit utiliser le bouton **"Charger Excel"** directement depuis l'interface du dashboard.
