---
title: "Assignment 3 - Stamping Identity"

categories:
  - blog
tags:
  - Jekyll
  - update
---

# Image Analysis of Stamps along the Silk Road



## Introduction

As someone who works in visual culture, I am very familiar with the traditional methods of visual analysis, which usually rely on close observation of formal properties. However concepts of ‘distant viewing’ bring a new way to think about visual media, one that also looks at mass amounts of images together. After reading the prompt, I felt a bit conflicted on what to focus on since in a way this assignment is perfect for me and my academic interests but that also made overwhelming. I eventually drew inspiration from iconography, which is a branch of art history that addresses identification, description and interpretation of the content of images. Icons are deeply connected with mass communication and I felt that there was a lot of potential for it to be studied with distant reading techniques. I decided to work on stamps, a common image with a very standardized angle/dimension, but which also depicts iconic images that are important to national identity. As stamps are signifiers of mail and trade, I chose to limit my scope to locations within our region and looked nations or locations along the Silk Road, that depict ‘ancient art’ in the 20th century. Using Orange Data Mining, I was able to create Image Grids and Confusion Matrixes that I can analyze. Distant Viewing Explorer allowed me to create captions for some of the stamps that I also assessed. This project taught me a lot about stamps, through traditional research but also come to interesting conclusions through these digital tools. 

All data and results can be seen [here](https://drive.google.com/drive/folders/1l-uiz3k25vsmXrdIu4p_N14jmqP7lseD?usp=drive_link).

## Background

Using the online archive, [stampworld.com](http://stampworld.com) , I was able to access a variety of different stamps from all over the world. Although I knew I wanted to look at iconic images in stamps from different countries, it was very overwhelming to  find a specific focus. Originally I wanted to focus on connections between colonies and empires, since postage stamps were part colonialism. I also considered looking at charity stamps, a specific type of postage stamp that has a surcharge to support national charities or funds. However, I still found it difficult to work on creating a consistent corpus that had a clear theme. I also explored the website a lot as it has a very unique and sometimes inconsistent categorization, as it relies crowdsourcing from enthusiast, similar to wikipedia. Many of the ‘nation’ tags were confusing since the same area was called many different names during different colonial rules. 

##### Building the Corpus

While browsing on the website, I found a tag called [“Ancient Art”](https://www.stampworld.com/en/stamps/global/all/) that held 1009 stamps. Using Image Downloader, I saved all the stamps that represent nations along the Silk Road. I was flexible on the boundaries of the Silk Road, including many nations/reigns within the general area. I saved every image and named the file after the country and year of the stamps. I also categorized the images by origin and subject. Origin referred to the nation represented and includes Africa, East Asia, South Asia, South East Asia, Gulf, West Asia. This was a relatively straight forward category with the only adjusted distinction being between Gulf and West Asia to refer to Arab or Persian countries and Turkish or Mediterranean (European) places. This was a later change I made since originally they were one category but it was extremely large and I adjusted it so that each tag has similar amounts of stamps so that the confusion matrix would work better. The second category is more subjective and refers to the content of style of the stamp and includes 5 tags such as Abstract, Architecture, Artifact, Drawing, and Portrait. Some of these images blurred the boundaries of these tags, e.g. a portrait of a bust that is also an artifact, but I made a personal judgement on which category felt the most representative.

## Orange Data Mining

##### Image Grids

In Orange, I uploaded my files first in one folder and tried different embedding models to create the Image Grid. I tried to use multiple models but many of them kept failing for me for some reason and in the end I was only able to get Painters and SqueezeNet to work. 

![Comparison between Embedding Models on uncategorized images](https://github.com/insiyam/insiyam.github.io/blob/9c13e0ec2c4d6f4423e918497fd6d9e0122f8488/assets/images/unclustered.imagegrid.comparison.png)

Comparison between Embedding Models on uncategorized images

The differences produced by these two models were instant. Painters definitely prioritized color, lightness, saturation and contrast. The diagonal line represents a visual divide between lighter images that use more white and with high contrast subjects that appear brighter and more saturated. The circle in the center right also seems to consist of many artifacts, especially those that have a high contrast with their background. The images seem to be aligned on mostly formalist qualities compared to SqueezeNet where I think there was more subject detection. The top left circle holds images that have full figured poses and the bottom center holds artifacts, especially ceramics. These groups seem to be based on the content of the image and do not share a more consistent formalist style, like Painters. The curved line across the right also seems to accurately capture the Abstract tag, compared to Painters, where the Abstract stamps blend in with drawings or other subjects that are in a similar color palette.  Similar to the MET project, the images that were placed next to each other can also pose some problems as they mix up humans, animals, or divine images, lacking the cultural sensitivity that is necessary for iconic images (Arnold & Tilton). Interestingly, both of these Image Grids do not capture any sense of national identity. The only example would be the grouping of the abstract or lighter stamps which tend to correlate with Islamic nations like Iran, Pakistan, and UAE, but this is still a weak grouping as it relies more on style and maybe even cultural values, rather than national icons. 

##### Hierarchical Clustering

Something I want to note is that the Image Grids also changed after uploading the clustered data. I am not really sure what caused that exactly since I don’t know how the test and score or class affected the hierarchical clustering. Between the two models, the hierarchical clustering did not change much in Origins but in Subject, Painters seems to have been identify stamp produced in specific countries and times while SqueezeNet seems more mixed. Even stamps that were produced in the together, with some variations, were split up by the SqueezeNet model, combining different years often.

![Section of hierarchical clustering from SqueezeNet in Subjects category](https://github.com/insiyam/insiyam.github.io/blob/d8932636aeccea0101a1aeb141cb98c2c513bbda/assets/images/clustering.closeup.png)



##### Confusion Matrix

After uploading the clustered data, I was also able to Test & Score and create some Confusion Matrices. 

![Confusion matrices for both categories and both models](https://github.com/insiyam/insiyam.github.io/blob/d8932636aeccea0101a1aeb141cb98c2c513bbda/assets/images/confusionmatrix.comparison.png)

Confusion matrices for both categories and both models

In Origin, both models performed similarly with higher accuracy only for Gulf and West Asia, with Painters having a very slight edge dominant tags while SqueezeNet in smaller tags. Painters consistently over predicted Guld and West Asia from almost all regions. SqueezeNet mixed up Gulf and West Asia more often but also predicted Africa or East Asia as Gulf more often. Interestingly, SqueezeNet did not misassign any South Asia stamps as Gulf, despite how Pakistan blended with Iran and UAE in the Image Grid. SqueezeNet also assigned higher accuracy for Africa, Easy Asia, South Asia and South East Asia.   

The algorithm performed better in Subject, despite it being a more subjective category. SqueezeNet performed better, predicting the most correct in each tag and also the less incorrect. Both models attributed Drawing most often to all categories. Both models also seem to struggle with distinguishing between portraits, drawings and artifacts, which makes sense as many stamps could be clustered in different tags and the decision was made on my personal opinion

## Distant Viewing Explorer

I chose to create captions for some of these stamps as I was curious to see how much the DV model was exposed to iconic or common images from different cultures. I picked a few stamps from the different Subject tags to see how famous sights, abstract designs, and portraits were identified. I was actually surprised by how poorly it performed and I would say only 6 out of the 25 images had a relatively accurate reading. 

##### Captions

![Selection of stamps and their predicted captions](https://github.com/insiyam/insiyam.github.io/blob/d8932636aeccea0101a1aeb141cb98c2c513bbda/assets/images/captions.comparison.png))

It seems that DV is better at recognizing realistic figures or colorful ornamental design. I was most surprised by its poor captioning of stamps from Egypt. I would think that these images were part of the “exclusionary visual canon” of the training model since Ancient Egyptian culture has been famous in the West throughout history and continues to be popular with many photographs and media showing these images or sites (Impett). The pyramids are such a famous site and silhouette that I thought the algorithm would identify it, however it fully missed its iconic status. The Egyptian images also have been identified as women, probably due to the ‘long hair’ of the traditional dress and the AI’s bias towards certain gender ideology.  I also noticed that the predictions tend to mention highly specific items like guns or fire hydrants that feel a bit random and make the caption seem ironic. It was also interesting to have the model evaluate the stamp from New Zealand as it shows a stylized lizard(?) but was identified as a bird somehow. 

Unfortunately, I was not able to figure out the python addons but I think if I was able to specify the types of input, the captions could have been more accurate.

## Conclusions

I really enjoyed working on this project and learning these new tools! Although I struggled a bit to get the hang of Orange I found it a very interesting way to assess images, departing from my usual analysis in my field. Although I really loved the UI of the Orange workflow and its visual layout rather than code, I found the specific steps a bit limiting. In particular, I was a bit frustrated by the lack of ability to adjust the view in the Image Grids. I wanted to include the labels of the images, since I had spent a lot of effort naming the country and year, and I was hoping to spot some trends especially based on time, but it would not show me the full title, only a few letters and I was not able to adjust it no matter what I tried. I also wish you could zoom in to the Image Grid or if the results saved as higher quality images. Since I had 226 images instead of the compulsory 75, the grid was a bit crowded and the individual images and text lost resolution and some stamps were not clear. 

The results from this project were also really interesting to me. Not only did I learn a lot about stamps but it was nice to see how diverse each country’s national identity can be represented, even within a short time frame. It seemed more like there were general stylistic trends of stamps rather than very specific or even stereotypical distinctions between figures or designs. 

## References

Impett, L., & Offert, F. (2022). There Is a Digital Art History. *Visual Resources*, *38*(2), 186–209. https://doi.org/10.1080/01973762.2024.2362466

Arnold, T., & Tilton, L. (2023). *Distant Viewing: Computational Exploration of Digital Images*. The MIT Press. [https://doi.org/10.7551/mitpress/14046.001.0001](https://doi.org/10.7551/mitpress/14046.001.0001)
