---
title: "Créer un site Hugo"
---

# Article tutoriel

[Créer un portfolio ou un blog sans programmer avec Hugo](https://aureliendossantos.github.io/post/2021/creer-un-site-avec-hugo/)

# Créer un site rapidement

La documentation de Hugo Book propose ces 4 lignes pour setup rapidement le site et copier le thème à la racine.

{{< tabs "installation" >}}
{{< tab "Linux" >}}
```sh
hugo new site mydocs; cd mydocs
git init
git submodule add https://github.com/alex-shpak/hugo-book themes/book
cp -R themes/book/exampleSite/content .
```
Puis changer le nom du thème dans le fichier config.
{{< /tab >}}
{{< tab "Windows ?" >}}
Il faut que je trouve l'équivalent du `;` et de `cp`
{{< /tab >}}
{{< /tabs >}}

# Publier avec GitHub Pages

## Créer le repo

En fonction de l'URL souhaitée, il faudra lui donner un nom différent au repo :

Adresse du site | Nom du repo
--- | ---
`https://<utilisateur>.github.io` | `<utilisateur>.github.io`
`https://<utilisateur>.github.io/<projet>` | `<projet>`

{{< tabs "creer-repo" >}}
{{< tab "Code source public" >}}
1. Créer un repo appelé `<utilisateur>.github.io` ou `<projet>`
2. Créer une branche `gh-pages`
3. Retourner dans la branche principale.
{{< /tab >}}
{{< tab "Code source privé" >}}
1. Créer un repo privé pour le code source. Son nom importe peu mais il doit être différent du repo public.
2. Créer un repo public pour le site final, appelé `<utilisateur>.github.io` ou `<projet>`. Il peut être créé depuis le site de GitHub et laissé vide pour le moment.
{{< /tab >}}
{{< /tabs >}}

## Créer le workflow

2. Créer le fichier `.github/workflows/gh-pages.yml`

```yml
name: GitHub Pages
on:
  push:
    branches:
      - master
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
        with:
          submodules: recursive
      - uses: benmatselby/hugo-deploy-gh-pages@master
        env:
          HUGO_VERSION: 0.84.4
          HUGO_EXTENDED: true
          TARGET_REPO: <...>
          TARGET_BRANCH: <...>
          TOKEN: ${{ secrets.HUGO_BUILD_TOKEN }}
```

{{< tabs "publier" >}}
{{< tab "Code source public" >}}
Mettre le nom du repo dans `TARGET_REPO` et écrire `TARGET_BRANCH: gh-pages`.
{{< /tab >}}
{{< tab "Code source privé" >}}
Mettre le nom repo public dans `TARGET_REPO` et supprimer la ligne `TARGET_BRANCH`.
{{< /tab >}}
{{< /tabs >}}

## Générer un token d'accès

1. Sur le site de GitHub, aller dans les paramètres de l'utilisateur, puis **Developer settings** > **Personal access tokens**
2. Générer un nouveau token et cocher le scope "repo".
3. Copier le token obtenu (il sera impossible de le voir de nouveau)
4. Retourner sur la page du repo, puis **Settings** > **Secrets** > **New repository secret**
5. Appeler le secret `HUGO_BUILD_TOKEN` et mettre comme valeur le token qu'on avait copié.
