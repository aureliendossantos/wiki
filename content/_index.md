---
title: Bienvenue
type: docs
BookToC: false
---

Ce wiki est avant tout destiné à mon usage personnel : j'y documente mon workflow et les outils que j'utilise afin de m'en souvenir plus tard. Cela dit, si vous y trouvez quelque chose d'utile, c'est tant mieux ! Et si vous vous y connaissez mieux que moi dans un de ces domaines, n'hésitez pas à m'envoyer vos suggestions.

## A propos

Ce site est construit avec le générateur de site statique [Hugo](https://gohugo.io/) et le thème [Hugo Book](https://github.com/alex-shpak/hugo-book) d'Alex Shpak.

Le code source est situé dans la branche `master` et un workflow GitHub Actions construit le site dans la branche `gh-pages`.

## Todo (peut-être)

- [ ] Alimenter en images. APIs:
    - Jeux : IGDB
    - CD : Discogs
    - Films : iMDB

## Documentation

### Front matter

```yaml
BookToC: false
bookHidden: true
bookFlatSection: true
bookCollapseSection: true
weight: 1
# musique
artistes:
year:
spotify: # oui/non
link: # markdown
youtube: # id
```

### Archetype

L'archetype est correctement détecté uniquement dans le dossier musique, donc :

```sh
hugo new content/musique/album.md
hugo new --kind musique content/musique/city-pop/album.md
```

### Problèmes connus

Bug de Hugo : commencer la page avec un shortcode ne fonctionne pas. Mettre en haut de la page :

```md
---
---
```
