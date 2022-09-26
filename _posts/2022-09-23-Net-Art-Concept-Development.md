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

Commented code below:

~~~js
let x = 1; //declare global variable 'x' where x = 1
let y = 1; //declare global variable 'y' where x = 1 
let easing = 0.03; //declare global variable 'easing',
                   //where easing = 0.03

function preload() //loads before setup
{
  pinkstar = loadImage('pinkstar.png') //load image 'pinkstar'
}

function setup() //happens once
{
  createCanvas(700, 500); //create canvas
                          //700 pixels wide 
                          //500 pixels tall
  imageMode(CENTER) //inteprets image parameters from its centre
  noCursor() //hides cursor from view
  
  soot = new Soot(); //declare 'Soot' as class name
}

function draw() //repeats
{
  background('pink'); //colour of canvas is pink
  image(pinkstar, mouseX,mouseY) //the pinkstar image is now the cursor
  
  soot.display(); //calls the 'display' function from Soot class
}

class Soot //class named 'Soot'
{
  //make circle follow the cursor's movement
  display() //custom function named 'display'
  
  {
  let cursorX = mouseX; //created a new variable named 'cursorX'
                        //refers to the mouse's x position
  let distancetoX = cursorX - x;
                  //created new variable named 'distancetoX'
                  //where it = to the mouse x's position on the canvas minus x
  x = x + distancetoX * easing;
  //x is defined as 1 + ( 0.01 x (mouse's x position -1))
  //the larger the easing value is the quicker the ellipse will move to cursor
  
  //same for the mouse's y position just using y
  let cursorY = mouseY;
  let distancetoY = cursorY - y;
  y = y + distancetoY * easing;
  
  ellipse(x, y, 50, 50); //create the ellipse 
  //call x and y in its parameters so that it follows the cursor
  noStroke();
  }
}
~~~

# Concept Developent 2 – Testing visual elements

The second goal was to utilise conditional logic to change the colour of the cursor star. As seen in the [soot scene]( https://www.youtube.com/watch?v=kL_1y5xdnWs), the soot spirits are being fed a variety of coloured stars (green, yellow, and pink). I want to invite this visual aspect in an interactive way; as the user moves the cursor around, the colour of the star changes. Once I was able to get the many of the built-in ellipse references in p5js to follow the cursor, I went ahead and imported my own soot spirit drawing into p5 and replaced the ellipse object with the image. I wanted to see how the visual elements interacted together before continuing the development of my concept

<iframe src="https://editor.p5js.org/vivianluh/full/cHRpIzZ_g" width="700" height="542"></iframe>

Commented code below:

~~~js
let x = 1; //declare global variable 'x' where x = 1
let y = 1; //declare global variable 'y' where x = 1 
let easing = 0.03; //declare global variable 'easing',
                   //where easing = 0.03

function preload() //loads before setup
{
  //load all images to get ready before set up runs 
  //images are also defined 
  pinkstar = loadImage('pinkstar.png') 
  greenstar = loadImage('greenstar.png')
  yellowstar = loadImage('yellowstar.png')
  sootspirit = loadImage('sootspirit.png')
}

function setup() //happens once
{
  createCanvas(700, 500); //create canvas
                          //700 pixels wide 
                          //500 pixels tall
  imageMode(CENTER) //inteprets image parameters from its centre
  noCursor() //hides cursor from view
  
  soot = new Soot(); //declare 'Soot' as class name
  star = new Star(); //declare 'Star' as class name
}

function draw() //repeats
{
  background('pink'); //colour of canvas is pink
  soot.display(); //calls the 'display' custom function from Soot class
  star.change(); //calls the 'change' custom function from Star class
}

//changing cursor class defined as 'Star'
class Star
{
  change() //custom function named 'change'
  {
    
    //conditional logic where if the mouse x position
    //is greater than half the width of the browser screen
    //the cursor will turn to a green star
    if (mouseX > windowWidth / 2)
    {
      image(greenstar, mouseX, mouseY)
    }
    
    //otherwise if the mouse x position
    //is greater than a third of the browser screen
    //the cursor will turn to a yellow star
    else if(mouseX > windowWidth /3)
    {
      image(yellowstar, mouseX, mouseY)
    }
    
    //otherwise the mouse will turn to a pink star
    else
    {
      image(pinkstar, mouseX, mouseY)
    }
  }
}

class Soot //class named 'Soot'
{
  //make circle follow the cursor's movement
  display() //custom function named 'display'
  
  {
  let cursorX = mouseX; //created a new variable named 'cursorX'
                        //refers to the mouse's x position
  let distancetoX = cursorX - x;
                  //created new variable named 'distancetoX'
                  //where it = to the mouse x's position on the canvas - x
  x = x + distancetoX * easing;
  //x is defined as 1 + ( 0.01 x (mouse's x position -1))
  //the larger the easing value is the quicker the ellipse will move to cursor
  
  //same for the mouse's y position just using y
  let cursorY = mouseY;
  let distancetoY = cursorY - y;
  y = y + distancetoY * easing;
  
  image(sootspirit, x, y)//place the image
  //call x and y in its parameters so that image follows the cursor
  noStroke();
  }
}
~~~

# Concept Developent 3 – A bunch of circles follows the cursor 

The third goal was to make an array where the canvas can call a bunch of circles from the array to appear on the screen randomly, and all of them collectively can follow the mouse as the user moves it around. In this stage I came across a few problems, including the use of global variables vs not using global variables, and the difference between x and this.x. With the help of Thomas, my lecturer, I was able to fix the problem. 

The first problem was that when I was trying to push the array and increase the number of circles appearing, the circles were being created, however they were appearing in the same exact spot and applying the same transformation because a global variable was used. Instead of this, the variables of x, and y (which I wanted the value to be randomised), and its easing were declared in the for loop for my array to combat this.

<iframe src="https://editor.p5js.org/vivianluh/full/zRD8aUgA8" width="700" height="542"></iframe>

Commented code below:

~~~js
let soot = [] //declare global variable 'soot'
              //where 'soot' is an empty array

function preload () { //loads before setup
  pinkstar = loadImage ('pinkstar.png') //load image 'pinkstar'
}

function setup () { //happens once
  createCanvas(700, 500) //create canvas
                          //700 pixels wide 
                          //500 pixels tall
  imageMode (CENTER)//inteprets image parameters from its centre
  noCursor () //hides cursor from view
  
  
  //a for loop that states;
  //variable named 'i' = 0 where i sets up the array contents
  //if i is less than 16
  //then another ellipse will be added to the canvas 
  //therefore there will be 16 ellipses on the canvas
  for (let i = 0; i < 16; i = i + 1) { 
    
    //inside the for loop
    //the x position of the ellipse will be random 
    //the y position of the ellipse will be random
    //it's easing will move in 0.01 pixels
    let x = random (width)
    let y = random (height)
    let e = random (0.01)
    //declare the class 'Soot'
    //the global variable soot and its empty array is called
    //while calling its x, y, and e values
    soot[i] = new Soot (x, y, e)
  }
}

function draw () {//repeats
  
  background ('pink'); //colour of canvas is pink
  
  for (let i = 0; i < 16; i = i + 1) { //repeat the for loop content 
    soot[i].display(); 
    //the loop will iterate the custom function 'display' in the class 'Soot'
  }

  image (pinkstar, mouseX,mouseY) //the cursor is the pink star
}

class Soot { //the class named 'Soot'
  constructor (x, y, e) { //set up for x, y, and e values 
    //values are defined inside the for loop, which soot is defined 
    this.x = x
    this.y = y
    this.easing = e
  }
  
  //movement of ellipse following cursor
  display () {
    
    let distancetoX = mouseX - this.x
    //created new variable named 'distancetoX'
    //where it = to the mouse x's position on the canvas minus x
    
    this.x = this.x + distancetoX * this.easing
    //x is defined as 1 + ( 0.01 x (mouse's x position -1))
    //the larger the easing value is the quicker the ellipse will move to cursor
  
    
  //same for the mouse's y position just using y
    let distancetoY = mouseY - this.y
    this.y = this.y + distancetoY * this.easing

    ellipse (this.x, this.y, 50, 50) 
    //create the ellipse 
    //call x and y in its parameters so that it follows the cursor
    noStroke ()
  }
}
~~~
