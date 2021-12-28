---
title: "Visualize Circos images with Seadragon"
date: 2010-04-02T16:34:41+00:00
tags:
  - bioinformatics
  - visualization
---
[Circos](http://mkweb.bcgsc.ca/circos/) is a very powerful tool to visualize different types of data (expression, homology, etc) in circular fashion.

The software is capable of producing very large images if desired, suitable for posters. 

Actually, we can create large images for viewing online, since it's trivial to view them with Seadragon.

Below is an example from Circos tutorial (I modified the config file to obtain large image) (*EDIT: Since the seadragon page was very slow to respond, I just included the embed URL*S)

```html
<script src="http://seadragon.com/embed/yhz.js?width=auto&height=400px"></script>
```

Original image is located [here](/img/circos-tutorial-huge.png).

PS: Author of Circos, Martin Krzywinski has more interesting software listed in [his page](http://mkweb.bcgsc.ca/). And his lecture notes on [Data Mining and Analysis at the Command Line](http://mkweb.bcgsc.ca/perlworkshop/index.mhtml?code=2.1.2.4) is worth checking.
