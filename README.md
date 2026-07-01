# PBN Hugo Template

Template de blog statique basé sur Hugo + thème PaperMod, avec pipeline CI/CD GitHub Actions pour déploiement automatique sur 3 plateformes.

## Stack technique

- **Générateur** : Hugo + thème PaperMod
- **CI/CD** : GitHub Actions
- **Hébergement** : GitHub Pages / Vercel / Cloudflare Pages

## Pipeline de déploiement

Chaque `push` sur `main` déclenche automatiquement :

```
Push → Build Hugo → GitHub Pages
                 → Vercel
                 → Cloudflare Pages
                 → Ping sitemap Google
```

## Structure du projet

```
├── .github/workflows/deploy.yml   # Pipeline CI/CD
├── content/posts/                 # Articles de blog
├── static/
│   ├── CNAME                     # Domaine custom
│   └── robots.txt
├── archetypes/default.md          # Template article
└── config.toml                   # Configuration Hugo + SEO
```

## Ajouter un article

```bash
hugo new posts/mon-article.md
# Éditer le fichier, passer draft: false
git add . && git commit -m "article: mon-article" && git push
```

## Configurer un nouveau site depuis ce template

1. Forker ou dupliquer ce repo
2. Modifier `config.toml` : `baseURL`, `title`, `description`
3. Modifier `static/CNAME` avec le nouveau domaine
4. Configurer les secrets GitHub (voir ci-dessous)
5. Configurer le DNS chez le registrar

## Secrets GitHub requis

| Secret | Description |
|--------|-------------|
| `CUSTOM_DOMAIN` | Nom de domaine custom (ex: mon-blog.fr) |
| `VERCEL_TOKEN` | Token API Vercel |
| `VERCEL_ORG_ID` | ID organisation Vercel |
| `VERCEL_PROJECT_ID` | ID projet Vercel |
| `CLOUDFLARE_API_TOKEN` | Token API Cloudflare |
| `CLOUDFLARE_ACCOUNT_ID` | ID compte Cloudflare |
| `CLOUDFLARE_PROJECT_NAME` | Nom du projet Cloudflare Pages |

## DNS GitHub Pages

```
A     @    185.199.108.153
A     @    185.199.109.153
A     @    185.199.110.153
A     @    185.199.111.153
CNAME www  COMPTE.github.io.
```
