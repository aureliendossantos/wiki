---
---

{{< summary "ordinateurs/tour.md" >}}

# Installation

Setup souhaité et estimations :

- SSD1 (720/930Go)
    - Documents (projets et programmes ~30Go)
    - Appdata (~40Go)
    - Tous les programmes sauf jeux (~150Go)
    - Montage vidéo et Cache Adobe (~300Go)
    - Jeux (~200Go)
- HDD (1650/1800Go)
    - Téléchargements (~100Go)
    - Musique (~100Go)
    - Images (~25Go)
    - Vidéos (~500Go)
    - Jeux (~300Go)
    - Documents de sauvegarde (Archives de montage vidéo, Sauvegarde Medion, sauvegardes PlayStation... ~400Go)
    
- HDD supplémentaire débranché: Sauvegardes

> Installer sans brancher le HDD pour éviter qu'il mette des trucs dessus

1. Un coup de [Disassembler0/Win10-Initial-Setup-Script](https://github.com/Disassembler0/Win10-Initial-Setup-Script) même so le projet est archivé depuis mai 2020. Il faut s'attendre à ce que certaines choses ne fonctionnent plus, et trouver une alternative sur le long terme, mais de toute façon, on passe bientôt à Windows 11.

2. [mon pack winstall](https://winstall.app/packs/n2nYi4bXD). winget installe certains programmes avec des paramètres indésirables :
    - git ajoute des options inutiles au menu clic droit
    - VS Code n'ajoute pas "Ouvrir ce dossier avec Code" alors que je le voudrais

3. Auto-login en ouvrant `netplwiz` et en décochant la case "Les utilisateurs doivent entrer un mot de passe". Si elle n'est pas présente, désactiver Windows Hello dans Paramètres > Comptes > Options de connection > Autoriser uniquement la connexion à Windows Hello.
