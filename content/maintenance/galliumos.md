---
title: "GalliumOS"
---

# GalliumOS

{{< summary "ordinateurs/acer-chromebook-cb3.md" >}}

# Installation

Version Baytrail. L'installation a planté ; relancer sans se connecter à Internet a réglé le problème.

Espace libre après installation : 10 GB.

Pour régler l'erreur suivante lors des mises à jour :

```
W: GPG error: http://ppa.launchpad.net/appgrid/stable/ubuntu bionic InRelease: The following signatures couldn't be verified because the public key not available: NO_PUBKEY 241FE6973B765FAE
E: The repository 'http://ppa.launchpad.net/appgrid/stable/ubuntu bionic InRelease' is not signed."sudo apt -qq update" returned an error. Proceed with caution.
```

```sh
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 241FE6973B765FAE
```

## Programmes utiles via apt

`git, nodejs, npm`

```sh
sudo apt install snapd
```

Redémarrer la session utilisateur ou l'ordinateur

```
snap install hugo --channel=extended
```

Snap est nécessaire, au moins pour Hugo, mais éviter de l'utiliser quand il y a une alternative : il semble que cela prenne plus de place et de ressources.

# Nettoyer

```sh
# Voir la taille du dossier
du -sh /var/cache/apt/archives
sudo apt-get clean
```
