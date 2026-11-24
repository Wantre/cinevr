<p align="center">
  <a href="https://cinevr.net"><img src="docs/banner.svg" alt="CineVR : votre cinéma, chez vous et en VR. Médiathèque auto-hébergée, salle VRChat, accès sur invitation." width="100%"></a>
</p>

<p align="center">
  <a href="https://cinevr.net"><img src="docs/btn-visiter.svg" alt="Visiter CineVR" height="52"></a>&nbsp;&nbsp;
  <a href="https://wantre.github.io/cinevr/"><img src="docs/btn-vitrine.svg" alt="Voir la vitrine" height="52"></a>
</p>

<p align="center"><b>CineVR</b> est une médiathèque personnelle hébergée sur un serveur à la maison.<br>
Elle range films, séries, animations et lectures, puis les ouvre dans le navigateur, sur le téléphone,<br>et dans une salle de cinéma VRChat où l’on regarde ensemble.</p>

<p align="center"><sub>Ce dépôt est une vitrine : le code de CineVR reste privé. L’accès au site se fait sur invitation.</sub></p>

---

## Trois écrans, une seule collection

Le même compte, la même liste et la même progression. On commence au salon, on continue dans le train, on finit dans la salle VR avec les amis.

<p align="center"><img src="docs/bureau.webp" alt="Maquette de CineVR sur ordinateur : menu latéral, recherche, vidéo à reprendre, ajouts récents et séries." width="100%"></p>

<table>
  <tr>
    <td width="34%" align="center"><img src="docs/mobile.webp" alt="Maquette de CineVR sur téléphone : lecteur en cours et liste des épisodes." width="100%"></td>
    <td width="66%" align="center"><img src="docs/casque-vr.webp" alt="Illustration : la salle de cinéma CineVR dans VRChat, vue depuis un casque." width="100%"></td>
  </tr>
  <tr>
    <td align="center"><sub>Sur téléphone</sub></td>
    <td align="center"><sub>Dans le casque, salle VRChat</sub></td>
  </tr>
</table>

<p align="center"><sub>Maquettes reconstituées d’après l’interface. Titres et visuels d’exemple.</sub></p>

## Ce que fait CineVR

<p align="center"><img src="docs/fonctions.webp" alt="Les fonctions de CineVR : catalogue, reprise de lecture, salons, thèmes, lecteur adaptatif, connexion rapide et profils." width="100%"></p>

| | |
|---|---|
| **Catalogue** | Films, séries rangées par saison et par épisode, animation et lecture en chapitres. Miniatures générées par FFmpeg, fiches complétées automatiquement. |
| **Reprise** | La position est enregistrée toutes les 10 secondes, sur chaque appareil. |
| **Salons** | Regarder ensemble à distance : salons de visionnage, amis, chat dans la salle, lecture synchronisée. |
| **Thèmes** | Des thèmes visuels changent les couleurs du site. |
| **Lecteur** | Flux HLS : la qualité suit la connexion, avec sous-titres. |
| **Connexion rapide** | Un code à 6 chiffres affiché sur un appareil déjà connecté ouvre la session sur la télé ou le casque. |
| **Profils** | Ma liste, favoris, historique et progression propres à chaque compte ; annonces et sondages sur l’accueil. |

## La salle VRChat

<p align="center"><img src="docs/salle-vr.webp" alt="La salle VRChat de CineVR et le panneau Unity Setup VRChat World." width="100%"></p>

1. **Glisser le dossier** `CineVR_VRChat` dans les Assets d’un projet de monde VRChat (Unity).
2. **Ouvrir** le menu *CineVR → Setup VRChat World*.
3. **Générer le monde** : l’écran, le catalogue et les scripts UdonSharp se posent.
4. **Entrer dans la salle** : on choisit une vidéo, elle se lance sur l’écran pour tout le monde.

## Architecture

<p align="center"><img src="docs/architecture.svg" alt="Architecture : le serveur maison (application Python, SQLite, FFmpeg, médiathèque) passe par Caddy puis Cloudflare jusqu’à cinevr.net, qui sert le navigateur, le téléphone et le monde VRChat. Connexion par Discord, Instagram ou code à 6 chiffres." width="100%"></p>

Pas d’hébergeur ni de stockage loué : un PC Windows à la maison fait tout tourner. Caddy chiffre en HTTPS avec Let’s Encrypt, Cloudflare protège le domaine par un tunnel.

## Accès privé

<p align="center"><img src="docs/acces-prive.webp" alt="Sécurité : liens signés qui expirent, connexion Discord et Instagram, CineVR Shield, HTTPS, journal d’audit, accès sur invitation." width="100%"></p>

- **Liens signés** HMAC-SHA256 à durée limitée pour chaque lecture.
- **Connexion** Discord ou Instagram (OAuth2), ou code à 6 chiffres.
- **CineVR Shield**, application Windows en .NET : échanges chiffrés ECDH + AES-256-GCM.
- **Journal d’audit** des actions d’administration ; pas d’inscription publique.

## Technologies

<p align="center">
  <img alt="Python" src="https://img.shields.io/badge/Python-0b0b10?style=for-the-badge&logo=python&logoColor=eab308">
  <img alt="Flask" src="https://img.shields.io/badge/Flask-0b0b10?style=for-the-badge&logo=flask&logoColor=eab308">
  <img alt="FastAPI" src="https://img.shields.io/badge/FastAPI-0b0b10?style=for-the-badge&logo=fastapi&logoColor=eab308">
  <img alt="SQLite" src="https://img.shields.io/badge/SQLite-0b0b10?style=for-the-badge&logo=sqlite&logoColor=eab308">
  <img alt="FFmpeg" src="https://img.shields.io/badge/FFmpeg-0b0b10?style=for-the-badge&logo=ffmpeg&logoColor=eab308">
  <img alt="Caddy" src="https://img.shields.io/badge/Caddy-0b0b10?style=for-the-badge&logo=caddy&logoColor=eab308">
  <img alt="Let’s Encrypt" src="https://img.shields.io/badge/Let%E2%80%99s_Encrypt-0b0b10?style=for-the-badge&logo=letsencrypt&logoColor=eab308">
  <img alt="Cloudflare" src="https://img.shields.io/badge/Cloudflare-0b0b10?style=for-the-badge&logo=cloudflare&logoColor=eab308">
  <br>
  <img alt="Discord" src="https://img.shields.io/badge/Discord-0b0b10?style=for-the-badge&logo=discord&logoColor=eab308">
  <img alt="Unity" src="https://img.shields.io/badge/Unity-0b0b10?style=for-the-badge&logo=unity&logoColor=eab308">
  <img alt="VRChat" src="https://img.shields.io/badge/VRChat-0b0b10?style=for-the-badge&logo=vrchat&logoColor=eab308">
  <img alt=".NET" src="https://img.shields.io/badge/.NET-0b0b10?style=for-the-badge&logo=dotnet&logoColor=eab308">
  <img alt="JavaScript" src="https://img.shields.io/badge/JavaScript-0b0b10?style=for-the-badge&logo=javascript&logoColor=eab308">
  <img alt="HTML5" src="https://img.shields.io/badge/HTML5-0b0b10?style=for-the-badge&logo=html5&logoColor=eab308">
  <img alt="CSS" src="https://img.shields.io/badge/CSS-0b0b10?style=for-the-badge&logo=css&logoColor=eab308">
</p>

---

<p align="center">
  <a href="https://cinevr.net"><img src="docs/btn-visiter.svg" alt="Visiter CineVR" height="52"></a>
</p>

<p align="center">
  <a href="https://github.com/Wantre">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="docs/wantre-lockup.svg">
      <source media="(prefers-color-scheme: light)" srcset="docs/wantre-lockup-black.svg">
      <img alt="Fait par Wantre" src="docs/wantre-lockup.svg" height="40">
    </picture>
  </a><br>
  <sub>Fait par <a href="https://github.com/Wantre">Wantre</a></sub>
</p>

<p align="center"><sub>Vitrine de présentation. Interface reconstituée, titres et visuels d’exemple ; aucune œuvre de tiers n’est montrée. Logos des technologies : Simple Icons, marques de leurs propriétaires. Tous droits réservés.</sub></p>
