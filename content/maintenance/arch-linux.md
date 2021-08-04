---
---

{{< summary "ordinateurs/acer-chromebook-cb3.md" >}}

# Installation

## Choix de la distribution

C'est marrant d'apprendre à installer Arch Linux et à le personnaliser. Mais ce n'est pas ma seule passion dans la vie non plus. Après 2 ou 3 jours, j'avais envie de passer à autre chose et il me manquait encore des choses à configurer, donc au lieu de m'embêter, j'ai préféré choisir une distribution complète basée sur Arch.

{{< columns >}}

### Manjaro i3

Installation simple et rapide.

Après installation (avec swap file) 8 Go de libre restants.

<--->

### EndeavourOS i3

Utilise i3-gaps. Installation très lente et moche, qui ne met pas en confiance.

31/07/2021 : Ne fonctionne pas sur mon Acer Chromebook. Il y a un login screen puis le bureau ne se démarre pas, sans aucun message d'erreur...

{{< /columns >}}

## Setup Manjaro

1. Installer Oh My Zsh :

    1. Changer le shell pour Zsh : `chsh -s $(which zsh)`
    2. Déco reco
    3. Vérifier : `echo $SHELL`
    4. Installer [Oh My Zsh](https://ohmyz.sh)

2. Installer yay : `sudo pacman -S yay`

3. Copier mes fichiers de config i3 et i3status

4. `yay -S xorg-xbacklight` pour régler la luminosité

5. Installer Chrome et VS Code (bin)

6. `code .config/mimeapps.list` Remplacer les `Pale Moon.desktop` en `google-chrome.desktop`

7. Personnaliser Conky : le thème utilisé par défaut est "conky maia". `locate conky_maia` et modifier avec `sudo nano`.

La solution pour régler l'audio sur le wiki Arch du CB3-131 n'a pas marché.

# Mises à jour

```sh
<pacman/yay> -Syu
```

## Erreur de keyring sur Pacman

Sometimes if a user doesn't update their system for a long time, this keyring might expire. The keyring can also get corrupted for some reason. To solve basic keyring issues do the following:

```sh
# Resynchronise with the Manjaro repository servers
# to ensure that everything is up to date
sudo pacman -Syy
# Refresh and update the signature keys
sudo pacman-key --refresh-keys
# Reload the signature keys
sudo pacman-key --populate archlinux manjaro
```
The three commands above should solve most (basic) keyring issues.[^keyring]

[^keyring]: [How to solve keyring issues in Manjaro](https://archived.forum.manjaro.org/t/how-to-solve-keyring-issues-in-manjaro/4020)

### Problème lié

Après avoir fait cela et fait une mise à jour, j'ai eu des problèmes que je soupçonne être ceci : https://www.reddit.com/r/ManjaroLinux/comments/lqbw0n/my_manjaroi3_just_became_archlinuxlol_and_all_of/

après avoir fait `pacman-mirrors -c all` j'ai dû effectuer de nouvelles mises à jour mais cela n'a pas réglé entièrement mon problème ; j'ai préféré réinstaller.

# Nettoyer espace disque

Vider la corbeille

Vérifier un dossier : `ncdu`

```sh
yay -Scc
npm cache clean --force  
```
