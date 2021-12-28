---
# followed the instructions at https://wowchemy.com/docs/widget/slider/
# but still overlay is pretty ugly
widget: slider
headless: true
weight: 1

interval: false
height: 400px
item:
  - title: Announcement
    content: 'R package [ceRNAnetsim](https://github.com/selcenari/ceRNAnetsim) written by our lab member Selcen is alive! Please give it a spin with `devtools:: install_github(\"selcenari/ceRNAnetsim\")`'
    align: center
    overlay_color: '#555'
    #Image path relative to your `static/img/` folder.
    overlay_img: headers/bubbles-wide.jpg  
    overlay_filter: 0.5
    cta_label: 'Get Started'
    cta_url: 'https://github.com/selcenari/ceRNAnetsim/'
    cta_icon_pack: fas
    cta_icon: graduation-cap
---
