---
layout: post
title: "Magical Celeste"
subtitle: "A Kontakt instrument inspired by the magic of Harry Potter"
date: 2021-06-28 16:46:00 +0200
tags: [Kontakt instruments]
background: '/img/posts/06.jpg'
---

I think that ever since I heard ["Hedwig's Theme"](https://youtu.be/I35XMs5J7II) for the first time I have been curious as to what instrument it really is that plays the melody. I've heard the instrument [celeste](https://www.vsl.co.at/en/Percussions/Celesta) mentioned numerous times, but most samples of a celeste don't sound quite like the Harry Potter score. I stumbled across [a fascinating analysis](https://filmmusicnotes.com/2013/04/13/john-williams-themes-part-6-of-6-hedwigs-theme-from-harry-potter/) of the theme that also mentioned that the sound is electronically manipulated. Some further digging [revealed](https://youtu.be/eOCJkrbQWaE) that the sound used in the Harry Potter score is actually a mix of a sampled celeste and a Yamaha DX7 playing a sine wave. There even seems to be a commercial Kontakt instrument called ["Randy’s Celeste"](https://cinesamples.com/product/randy-s-celeste) based on this sound. So, fascinated by this sound I wanted to try to recreate it and see what happens when different aspects and components of the sound are varied.

I found some [free public domain celeste samples](https://freesound.org/people/stamperadam/packs/6166/) and made my own wave file containing a sine wave. I edited a few of the celeste samples to remove some clicks and adjusted the starting position, tuning and loudness of every sample according to the [EBU R128 measurement method](https://tech.ebu.ch/loudness). I built the Kontakt instrument using [Kontakt version 6.5.3](https://www.native-instruments.com/en/products/komplete/samplers/kontakt-6/) and learned the basics of [KSP scripting](https://www.native-instruments.com/en/products/komplete/samplers/kontakt-6/downloads/) along the way. The user interface I built using [Canva](https://www.canva.com/).

<!-- ![screenshot](/images/screenshot.png) -->

<img class="img-fluid" src="/img/posts/magical-celeste-screenshot.png" alt="Screenshot">

The features of this instrument are now the following:
- Celeste samples
  - The transition between the two velocity layers of the celeste samples can be adjusted using the normal/medium/soft buttons. Soft means that only the soft velocity layer is used.
  - Volume
  - High pass filter
  - Low pass filter
  - Stereo width
  - ADSR including attack curve and hold
- Sine wave
  - Volume
  - LFO level and frequency
  - ADSR including attack curve and hold
- Reverb
  - Wet level
  - Dry level

I wanted to use the snapshot feature of Kontakt to include a few different presets, but it seems that snapshot files would have to be manually placed in a [separate folder](https://forum.cockos.com/showthread.php?t=213875), if I am not mistaken. So instead I made some copies of the nki file, each with different settings.

To download this Kontakt instrument, go to [https://github.com/bustad/magical-celeste](https://github.com/bustad/magical-celeste).

Enjoy! :musical_note: :musical_keyboard: :smile:
