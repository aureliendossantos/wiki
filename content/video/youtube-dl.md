---
title: "youtube-dl"
weight: 3
---

## `%appdata%/youtube-dl/config.txt`

```
-o "E:/Creative Cloud Files/youtube-dl/%(title)s.%(ext)s"
-f bestvideo[ext=mp4]+bestaudio[ext=m4a]/best
```

[Mon tutoriel](https://aureliendossantos.github.io/post/2020/telecharger-des-videos-youtube/)

## Outil perso

Un petit fichier Batch qui propose une commande plus succinte :

- `yt <lien>` pour utiliser les paramètres de qualité de youtube-dl,
- `yt <lien> 1080` pour télécharger en 1080p maximum,
- `yt <lien> mp4` pour télécharger la meilleure piste vidéo disponible au format MP4 (qui ne dépassera généralement pas 1080p, puisque YouTube semble préférer d'autres formats pour la 4K).

Le code est un peu clunky car Batch pense que le `=` du lien YouTube sépare deux arguments. Je ne sais pas comment youtube-dl règle ce problème. Donc je ne me suis pas embêté : la commande attend deux arguments qui sont ensuite réunis avec un `=`, ce qui fait que l'outil n'accepte que les liens de vidéo YouTube.

### `yt.cmd`

```batch
@echo off
IF "%~3"=="1080" goto 1080
IF "%~3"=="mp4" goto mp4
IF "%~2"=="" goto error

:normal
echo.
echo Downloading at highest quality available...
echo NOTE: Use "yt url 1080" to download at 1080p max.
echo.
youtube-dl %1=%2
goto end

:1080
echo.
echo Downloading at 1080p...
echo.
youtube-dl -f "bestvideo[height<=1080]+bestaudio/best" %1=%2
goto end

:mp4
echo.
echo Downloading video in MP4 (probably 1080p)...
echo.
youtube-dl -f "bestvideo[ext=mp4]" %1=%2
goto end

:error
echo This isn't a YouTube video. Please use youtube-dl directly.

:end
```
