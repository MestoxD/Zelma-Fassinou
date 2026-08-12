# Portfolio — S.E. Mme Zelma Yollande Nobre Fassinou

Site officiel de la Représentante Résidente de la CEDEAO au Sénégal.
Site statique, bilingue français / anglais, en un seul fichier `index.html`
(images, logos, styles et animations embarqués).

---

## Contenu du dossier

| Fichier | Rôle |
|---|---|
| `index.html` | Le site complet (accueil + page Activités) |
| `favicon.ico` | Favicon multi-tailles (16 → 256 px) |
| `favicon.png` | Favicon PNG haute définition (512 px) |
| `apple-touch-icon.png` | Icône iOS (ajout à l'écran d'accueil) |
| `icon-192.png` / `icon-512.png` | Icônes Android / PWA |
| `og-image.jpg` | Aperçu affiché lors des partages (WhatsApp, LinkedIn, X…) |
| `site.webmanifest` | Manifeste d'installation mobile |
| `vercel.json` | URLs propres + en-têtes de cache et de sécurité |
| `robots.txt` / `sitemap.xml` | Référencement |

---

## Déploiement sur Vercel via GitHub

### 1. Créer le dépôt

Placez **tous les fichiers de ce dossier à la racine du dépôt** — surtout pas
dans un sous-dossier, sinon `favicon.ico` et `og-image.jpg` ne seront pas trouvés.

```bash
git init
git add .
git commit -m "Portfolio S.E. Mme Zelma Yollande Nobre Fassinou"
git branch -M main
git remote add origin https://github.com/VOTRE-COMPTE/VOTRE-DEPOT.git
git push -u origin main
```

### 2. Importer sur Vercel

1. Sur [vercel.com](https://vercel.com) → **Add New → Project** → sélectionnez le dépôt.
2. **Framework Preset : Other** (aucun framework, c'est un site statique).
3. Laissez **Build Command** et **Output Directory** vides.
4. **Deploy**.

Le site est en ligne en moins d'une minute.

---

## Pourquoi l'URL n'affiche pas `.html`

Deux mécanismes se combinent :

- Le fichier s'appelle **`index.html`** : Vercel le sert automatiquement à la
  racine, donc l'adresse est `votre-domaine.vercel.app/` et non
  `…/portfolio.html`.
- `vercel.json` active **`cleanUrls: true`** : si une autre page `.html` est
  ajoutée plus tard (ex. `presse.html`), elle sera servie sur `/presse`, et
  toute visite de `/presse.html` sera redirigée vers `/presse`.

Le site étant en une seule page avec bascule interne vers les Activités,
il n'existe de toute façon qu'une seule URL.

## Le favicon

Il est déclaré en trois formats (`.ico`, `.png`, icône Apple) avec des chemins
relatifs, ce qui fonctionne aussi bien en local qu'une fois déployé. Si vous ne
le voyez pas immédiatement après la mise en ligne, videz le cache du navigateur
ou ouvrez la page en navigation privée : les navigateurs conservent longtemps
l'ancien favicon.

---

## Après le déploiement

1. Dans `robots.txt` et `sitemap.xml`, remplacez `VOTRE-DOMAINE.vercel.app`
   par l'adresse réelle du site.
2. Pour un nom de domaine personnalisé : Vercel → **Settings → Domains**.
3. Testez l'aperçu de partage sur
   [opengraph.xyz](https://www.opengraph.xyz) en collant l'URL du site.

## Modifier le site

Tout est dans `index.html`. Quelques repères utiles :

- **Textes** : objet `I18N` (versions `fr` et `en`) au début du script.
- **Parcours** : tableau `PARCOURS`.
- **Activités** : tableau `ACTIVITES`.
- **Vision et priorités** : tableaux `VISION` et `PRIORITES`.
- **Couleurs** : variables CSS `--vert`, `--or`, `--ivoire` en haut du fichier.

Après modification : `git add . && git commit -m "mise à jour" && git push`.
Vercel redéploie automatiquement.
