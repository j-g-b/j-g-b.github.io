---
layout: post
title: "Music in the wild"
author: "Jordan Bryan"
categories: journal
tags: [documentation,sample]
image: fox.png
---

Neural networks have become popular tools for transfering the style of one artistic work or photograph to another. Methods for performing style transfer are distinguished from one another by features of the neural network's design as well as the loss function that guides network updates. In a recent project, I teamed up with [Alessandro Zito](https://stat.duke.edu/people/alessandro-zito-0) to use a method based on the theory of **optimal transport** to transfer visual elements of musical instruments onto the forms of animals. The method was developed by Vince Marron and is available on his [GitHub Page](https://github.com/VinceMarron/style_transfer). The original photos used to produce the images in this post can be found at the links in the References section.

![alt text](https://github.com/j-g-b/j-g-b.github.io/raw/master/assets/img/dcoral2.jpg)

The artistic side of our work starts from a simple question: are musical instrument able to generate rhythm and motion even when they are not played? To test this, we fused the picture of several instruments with pictures of animals in resting poses (not caught during a particular motion). 

![alt text](https://github.com/j-g-b/j-g-b.github.io/raw/master/assets/img/scaterpillar.png)

Rather than simply combining the pictures, we wanted to recognize the existing patterns and shapes of the instruments and to use them to deconstruct and then reconstruct the resting animals. The decomposition gives a sense of motion that is typical of the paintings of Franz Marc and the Italian futurists (especially Umberto Boccioni), with an artistic process that is somehow similar to that of the early Piet Mondrian and, more broadly, Damien Hirst. All of these artists provided a vivid and dynamic image of movement that always came from the geometric segmentation of reality.

![alt text](https://github.com/j-g-b/j-g-b.github.io/raw/master/assets/img/ppanda.png)

Our instruments are tools to set the animal into motion, to transfer momentum onto its soul. When every melody stops all that remains is the mood of the listener. Thus, we want the instruments, at the end, to almost disappear. All they have to provide is a spark of life.

![alt text](https://github.com/j-g-b/j-g-b.github.io/raw/master/assets/img/tgiraffe.png)

# References

**Fox**

- [https://www.animalrescuediary.com/author/animalrescuediary_hs04ne/](https://www.animalrescuediary.com/author/animalrescuediary_hs04ne/)
- [https://wallpaperaccess.com/violin](https://wallpaperaccess.com/violin)

**Caterpillar**

- [https://www.flickr.com/photos/135741389@N02/48117574837](https://www.flickr.com/photos/135741389@N02/48117574837)
- [https://www.kesslerandsons.com/product/yanagisawa-solid-silver-tenor-sax/](https://www.kesslerandsons.com/product/yanagisawa-solid-silver-tenor-sax/)

**Giraffe**

- [https://www.pinterest.com/pin/119908408804479620/](https://www.pinterest.com/pin/119908408804479620/)
- [http://www.wright-music.com/rentals/school-year-trumpet-rental](http://www.wright-music.com/rentals/school-year-trumpet-rental)

**Panda**

- [https://www.wwf.gr/en/endangered-species/panda](https://www.wwf.gr/en/endangered-species/panda)
- [https://www.musictoyourhome.com/blog/how-to-clean-piano-keys-without-damage/](https://www.musictoyourhome.com/blog/how-to-clean-piano-keys-without-damage/)

**Coral**

- [http://www.drummertalk.org/2014/12/29/every-drum-yamaha-makes-in-one-kit-monsterkitmonday/](http://www.drummertalk.org/2014/12/29/every-drum-yamaha-makes-in-one-kit-monsterkitmonday/)
- [https://photos.com/featured/green-sea-turtle-over-coral-reef-georgette-douwma.html?product=poster](https://photos.com/featured/green-sea-turtle-over-coral-reef-georgette-douwma.html?product=poster)

**Code**

- [https://github.com/VinceMarron/style_transfer](https://github.com/VinceMarron/style_transfer)