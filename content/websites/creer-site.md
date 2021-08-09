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
{{< tab "Windows" >}}
```
hugo new site rando
cd rando
git init
git submodule add https://github.com/monkeyWzr/hugo-theme-cactus themes/cactus
Xcopy themes\cactus\exampleSite . /E
```
{{< /tab >}}
{{< /tabs >}}
