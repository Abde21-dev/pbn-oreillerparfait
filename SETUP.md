# PBN Hugo Template — Guide de déploiement

## 1. Cloner et configurer

```bash
git clone --recurse-submodules https://github.com/TON-COMPTE/pbn-hugo-template.git mon-site-pbn
cd mon-site-pbn
```

Modifier `config.toml` :
- `baseURL` → ton domaine
- `title` → nom du blog
- `description` → description SEO
- `robots.txt` → remplace VOTRE-DOMAINE.com

## 2. GitHub Secrets à configurer

Dans GitHub → Settings → Secrets → Actions :

| Secret | Valeur |
|--------|--------|
| `CUSTOM_DOMAIN` | ton-domaine.com |
| `VERCEL_TOKEN` | Token API Vercel |
| `VERCEL_ORG_ID` | ID org Vercel |
| `VERCEL_PROJECT_ID` | ID projet Vercel |
| `CLOUDFLARE_API_TOKEN` | Token API Cloudflare |
| `CLOUDFLARE_ACCOUNT_ID` | ID compte Cloudflare |
| `CLOUDFLARE_PROJECT_NAME` | Nom projet Cloudflare Pages |

## 3. Récupérer les tokens

### Vercel
1. vercel.com → Settings → Tokens → Create Token
2. `VERCEL_ORG_ID` et `VERCEL_PROJECT_ID` : dans `.vercel/project.json` après `vercel link`

### Cloudflare
1. dash.cloudflare.com → My Profile → API Tokens → Create Token
2. `CLOUDFLARE_ACCOUNT_ID` : dans l'URL du dashboard

## 4. Premier déploiement

```bash
git add .
git commit -m "init: premier site PBN"
git push origin main
```

Le pipeline se déclenche automatiquement → 3 déploiements simultanés.

## 5. Ajouter un article

```bash
hugo new posts/mon-article.md
# Édite le fichier, remplace draft: false
git add . && git commit -m "article: mon-article" && git push
```
