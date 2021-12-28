---
title: "View large images with Seadragon in personal pages"
date: 2010-04-01T03:50:00+00:00
tags:
  - visualization
---
Maybe you already watched the video regarding Seadragon given at TED (sorry only low resolution version was available)

{{< youtube PKwTurQgiak >}}

I just discovered that you can embed Seadragon into your own page. If you want to embed an image with enormous size, go to [Seadragon](http://seadragon.com/) page and paste URL of the image and it will create html embed script which you insert into your page's html code.

Below is the Seadragon view of space image of world at night: (*EDIT: Since the seadragon page was very slow to respond, I just included the embed URL*S)

```html
<script src="http://seadragon.com/embed/82q.js?width=auto&height=400px"></script>
```

Original image is located [here](http://techlab.scherdan.com/albums/satellite/NASA_satellite_photo_of_Earth_at_night_high_res_city_lights.jpg).

Here's another example (satellite image of Turkey):

```html
<script src="http://seadragon.com/embed/yf4.js?width=auto&height=400px"></script>
```

Original image is located [here](http://veimages.gsfc.nasa.gov/6878/Turkey.A2004096.0830.250m.jpg).