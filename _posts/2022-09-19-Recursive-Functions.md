---
layout: post
title:  "Recursion"
date:   2022-09-19 14:43:10 +1000
categories: jekyll update
---

A ‘new’ Javascript concept that was introduced and is to be employed somewhere in the Net Art piece is ‘Recursive Functions’. Like the concept of iteration that was introduced before, recursion is similar, however is not limited to the employment of for loops (that iteration may be). Recursion is the concept of branching self-reference , where it can draw itself, and then call itself again. 

![Imgur](https://i.imgur.com/jjdFIsQ.png)

To put into play the concept of recursion, I utilised the following [tutorial]( https://www.youtube.com/watch?v=jPsZwrV9ld0&ab_channel=TheCodingTrain) 
to employ the ideas introduced during [class]( http://thomas.capogre.co/rmit/ccs/2022/09/03/recursion.html) and aid in this experiment. 


<iframe src="https://editor.p5js.org/vivianluh/full/ZjHTjpxr2" width="400" height="442"></iframe>

Commented code below:

~~~js
function setup() 
{
  createCanvas(400, 400);
  //400 pixels wide
  //400 pixels tall
}

function draw() 
{
  background(0); //fill background black
  //call function drawCircle 
  //circle is located 200 pixels on x axis
  //circle is located 200 pixels on y axis
  //diameter of 200 pixels
  drawCircle(200, 200, 200)
}

//created custom 'drawCircle' function
//defined variables x, y, and d
function drawCircle(x, y, d)
{
  ellipse(x, y, d); //draw the ellipse
  if (d > 2) //conditional if diameter is greater than 2
    //draws the circle, then calls it again
  {
    //draw another circle to the right
    //x position is 0.5 pixels to the right
    //diameter is 0.5 pixels smaller than 200
    drawCircle(x + d * 0.5, y, d * 0.5);
    //draw another circle to the left
    //x position is 0.5 pixels to the left
    //diameter is 0.5 pixels smaller than 200
    drawCircle(x - d * 0.5, y, d * 0.5);
  }
~~~