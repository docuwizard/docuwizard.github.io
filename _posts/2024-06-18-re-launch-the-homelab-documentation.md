---
layout: post
title: Umzug und Umbau der Homelab Documentation
date: 2024-06-18 14:03 +0200
youtubeId: teV7XluaSl4
image:
  path: /assets/images/jekyll-logo-light-transparent.png
---

## Jekyll Re-Launch

![Light mode only](/assets/images/jekyll-logo-light-transparent.png){: .light }
![Dark mode only](/assets/images/jekyll-logo-dark-transparent.png){: .dark }

Der *Static-Site-Generator* **Jekyll** ist auf eine neue VM unter Proxmox umgezogen und hat bei dieser Gelegenheit eine Menge Ballast abgeworfen. Für den Leser von **Docu Wizard** vielleicht weniger interessant - für den Wizard aber eine _erhebliche Beschleunigung_ und damit Zeitersparnis.

>Ausserdem lassen sich neue `Posts` nun auch von überall aus einem Browser erstellen bzw. alte Posts redigieren.

> Das Github Repository wurde umgestellt und ist ab sofort nicht mehr öffentlich zu erreichen.
{: .prompt-info }

- [x] check _config.yml
- [ ] review style guide
- [ ] stay awesome!

<span style="color:green">This is a green text.</span>


[Github: jeffreymorganio/responsive-youtube-jekyll-tag ](https://github.com/jeffreymorganio/responsive-youtube-jekyll-tag)
{% youtube teV7XluaSl4 %}


[Github: nathancy/jekyll-embed-video](https://github.com/nathancy/jekyll-embed-video)
{% include youtubePlayer.html id=page.youtubeId %}

{%
  include embed/video.html
  src='https://nextcloud.srvu.de/s/HJ2RpdaZrRXN9dq/download/Final.mp4'
  types='ogg|mov'
  poster='poster.png'
  title='BMW R 1250 GS'
  autoplay=false
  loop=true
  muted=true
%}

{%
  include embed/video.html
  src='https://nextcloud.srvu.de/s/LxNKZPBzFKy8WRF/download/nexus.mp4'
  types='ogg|mov'
  poster='poster.png'
  title='Nexus'
  autoplay=false
  loop=true
  muted=true
%}