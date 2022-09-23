---
layout: post
title:  "Net Art Concept Development"
date:   2022-09-23 14:43:10 +1000
categories: jekyll update
---

The second project in my creative coding journey consists of creating a static site that uses Javascript concepts learnt so far to generate ‘effective complexity’ with the addition of using audio and/or interaction in the build. Effective complexity was explored in the first project of this journey, for which I have summarised it (in my own terms) as finding a balance between complete monotony and chaos, with these interactions between opposites inviting a somewhat ‘cute’ outcome. 

# Ideating – Ideating and Brainstorms

With these concepts in mind, I want to create a colourful interactive site that has a fun and playful feel to it as users click around the page. I drew a lot of my stylistic choices and visual elements from one of my all-time favourite animated films ‘Spirited Away’ directed by Hayao Miyazaki, especially the scene of the [soot spirits getting fed with stars](https://www.youtube.com/watch?v=kL_1y5xdnWs). The interaction between the soot spirits and the stars as they are being thrown has a chaotic feel to it, as they excitingly scurry to grab their share of the stars, while also being a cute interaction however part of their routine living as a soot spirit. 

![Imgur](https://i.imgur.com/OVtGhZF.png)

The brainstorm below consists of the first initial development, including drawing inspiration from the works of [Donut Birthday](https://qianqian-ye.com/Everyday/Day14/) by QianQian Ye and [On and Off](http://www.onandoff.org/). The inspiration drawn from these included the simple interactions, and the simple objectives that users achieve when interacting. The overall playful and colorful feel I wanted to convey is inspired by [Iuri’s portfolio](https://iuri.is/) display.

![Imgur](https://i.imgur.com/dhPocvR.png)

Javascript concepts were also explored when planning how I would apply my coding knowledge gained in the courses so far to achieve the goals for my interactive site. 

![Imgur](https://i.imgur.com/BUH4CFd.png)

# Assets 
All external assets I utilised in my code was created/drawn by me. Mainly I utilised procreate for this and used 100 x 100 pixels/200 x 200 pixels dimensions as these were recommended by p5js. 

![Imgur](https://i.imgur.com/B7fIS3R.jpg)


# Concept Developent 1 – A circle follows the cursor 
The first goal to creating my interactive site was to ensure an object can follow the mouse where it goes across the screen as the user moves it around. 

<iframe src="https://editor.p5js.org/vivianluh/full/boyR5s3pO" width="700" height="542"></iframe>


# Concept Developent 2 – A bunch of circles follows the cursor 

The second goal was to make an array where the canvas can call a bunch of circles from the array to appear on the screen randomly, and all of them collectively can follow the mouse as the user moves it around. In this stage I came across a few problems, including the use of global variables vs not using global variables, and the difference between x and this.x. With the help of Thomas, my lecturer, I was able to fix the problem. 

The first problem was that when I was trying to push the array and increase the number of circles appearing, the circles were being created, however they were appearing in the same exact spot and applying the same transformation because a global variable was used. Instead of this, the variables of x, and y (which I wanted the value to be randomised), and its easing were declared in the for loop for my array to combat this.

<iframe src="https://editor.p5js.org/vivianluh/full/zRD8aUgA8" width="700" height="542"></iframe>


# Concept Developent 3 – Changing visual elements

The third goal was to utilise conditional logic to change the colour of the cursor star. As seen in the [soot scene]( https://www.youtube.com/watch?v=kL_1y5xdnWs), the soot spirits are being fed a variety of coloured stars (green, yellow, and pink). I want to invite this visual aspect in an interactive way; as the user moves the cursor around, the colour of the star changes. Once I was able to get the many of the built-in ellipse references in p5js to follow the cursor, I went ahead and imported my own soot spirit drawing into p5 and replaced the ellipse object with the image. 

<iframe src="https://editor.p5js.org/vivianluh/full/cHRpIzZ_g" width="700" height="542"></iframe>

