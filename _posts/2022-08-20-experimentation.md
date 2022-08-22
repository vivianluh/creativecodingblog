---
layout: post
title:  "p5 Experimentation"
date:   2022-08-20 14:43:10 +1000
categories: jekyll update
---
In this section, I aim to apply a combination of Javascript concepts (variables, iteration, conditional logic, custom functions, arrays, classes) in small experimental p5 sketches. Hopefully, the knowledge gained from these exercises will combine to aid in creating the final ‘RMIT Creative Coding Specialisation’ banner design. Working in smaller experimental sections will also aid in troubleshooting any coding issues that I come across, and therefore will not jeopardise my final written p5 sketch for my banner.

# Experiment - Conditional Logic and creating custom Functions

In this exercise, I worked with font and colour together when applying conditional logic. While applying this concept, I also introduced several Javascript concepts such as declaring variables, and giving it values, and establishing custom functions to organise my p5 sketch.

<iframe src="https://editor.p5js.org/vivianluh/full/SNEcCOr6c" width="576" height="366"></iframe>

Commented code below:

~~~js
//Conditional Logic
//In this exercise I experimented with 
//conditional logic, applying the expression '>' as a relational operation
//defining variables
//creating custom functions and calling them

let museo //declare variable 'museo' (which is font name)

let col_1, col_2, col_3, col_4 //declare variable names for the colours

function preload () //load the font 'museo', getting it ready before function setup as it is an external file
{
  museo = loadFont ('fonts/Museo 700.otf')
}

function setup () //runs once, at the beginning
{
  createCanvas (576, 324) //created canvas
                          //576 pixels wide 
                          //324 pixels tall 
  
  col_1 = color (0, 0, 84) //gave variable a value colour of blue
  col_2 = color (230, 30, 42)//variable value colour of red
  col_3 = color (250, 200, 0)//variable value colour of yellow
  col_4 = color ('#FF5722')//variable value colour of orange
}

function draw () //loops forever after setup has run in the beginning
{
  background(col_1)//fill canvas blue
  rmit1(); //call custom function stated in rmit1
  rmit2(); //call custom function stated in rmit2
  rmit3(); //call custom function stated in rmit3
}

function rmit1(){
  fill (col_2)//make text red
  textFont (museo)//utilised defined variable
  textSize (200)//text size is 200 pixels
  text (`RMIT`, 50, 240)//place RMIT, on x value 50, y value 240
}

function rmit2() //defined a custom function
{
  
    //conditional logic statement if mouse along the x axis reaches more than 300 pixels then;
  
      if (mouseX > 300){ 
      fill (col_4) //make text orange
  textFont (museo)
  textSize (200)
  text (`RMIT`, 40, 240) //place another RMIT text, 10 pixels to the left of the rmit1 text. 
  }
}
  
function rmit3() //defined a custom function
{
  
    //conditional logic statement if mouse along the x axis reaches more than 300 pixels then;
   if (mouseX > 300){ 
      fill (col_3) //make text yellow
  textFont (museo)
  textSize (200)
  text (`RMIT`, 30, 240) //place yet another RMIT text, another 10 pixels to the left of rmit2.
  }
}
~~~

# Experiment - Variables

In this exercise, I worked on declaring a variable, initialising it with a value/data of some sought, and using it.  

<iframe src="https://editor.p5js.org/vivianluh/full/HExdWXcCg" width="400" height="442"></iframe>



Commented code below:

~~~js
//CREATION OF OWN VARIABLES
//1. DECLARE VARIABLE
//2. INITIALISE IT
//3. USE VARIABLE

let circleG = 100; //decare variable 'circleG'
                   //I have noted that I the variable to be a global variable, therefore it will not be initialised in function setup()

function setup() { //runs once
  createCanvas(400, 400); //creating canvas
                         //400 pixels wide 
                         //400 pixels tall
}

function draw() { //loops
  background('red'); //canvas is red
  noStroke() //my circle will have no stroke
  fill(255); //making circle white
  ellipse(200, 200, circleG); //create circle on canvas with a centered position
  
  //I have utilised circleG in order to manipulate the size of the circle
  circleG = circleG + 1
  //this singular statement, an assignment operation, where the right hand side is evaluated after every loop, adding a value of 1 after every loop. Function draw() is always looping.
}

function mousePressed(){ //a function is called once everytime the mouse is clicked
  
  circleG = 0;
}
//this function allows my variale of circleG to go back to a size of 0 once the mouse is pressed. 
~~~

# Experiment - Arrays and Iteration (For Loop)

In this exercise, I worked on utilising an array in my p5 sketch, and using those array values by calling for a for loop in the hopes of displaying those array values. As utilising for loops in conjunction with arrays was extremely hard for me to wrap myself around it, I specifically references this [tutorial]( https://www.youtube.com/watch?v=RXWO3mFuW-I&ab_channel=TheCodingTrain) to aid in this experiment.

<iframe src="https://editor.p5js.org/vivianluh/full/kL3TM4kGN" width="500" height="442"></iframe>

Commented code below:
~~~js
//ARRAYS AND ITERATION (FOR LOOP)

let nums = [100, 25, 46, 72]; //defined an array 'nums' and have placed 4 values inside array

function setup() {
  createCanvas(500, 400); //creating canvas
                         //500 pixels wide 
                         //400 pixels tall 
}

function draw() {
  background('red'); //red canvas

  //I have created a for loop, which instead of writing the code over and over again of ellipse(100, 200, nums[], nums[]) I can instead use a for loop. The variable name of i doesn't mean anything, it is just a convention. 
  
  //So with this for loop, I have started with 0, when the code runs, i then checks to see if i is smaller than 4, and if it is, 1 is added to it, therefore travelling to the next part of the array.
  for (var i= 0; i < 4; i = i + 1){
    noStroke() //no black outline
    fill(255); //fill the circle white
    ellipse(i*100 + 100, 200, nums[i]); 
    //the x position has to be i * 100 + 100 because i = 0, so  i * 100 = 0, (i + 1), so every iteration, it will be 100, 200, 300, 400. We add another 100 pixels to move them into the canvas (order of operations).
    
    //y position = 200, which is middle of canvas
    
    //z (the size) takes note of the array 'nums' values while taking in consideration the information in the for loop.
    
  }
}
~~~

# Experiment - Classes

In this exercise, I worked on utilising classes as a way to encapsulate data and its functionality of an object and call upon it in the function draw() section. The main concepts that I need to remember is to ensure the class has a constructor if declaring any variables in that class, as well as utilising ‘this’ when declaring the variable’s value. To aid in this introductory exercise with classes, I heavily referenced this [tutorial]( https://www.youtube.com/watch?v=T-HGdc8L-7w&ab_channel=TheCodingTrain).

<iframe src="https://editor.p5js.org/vivianluh/full/OvhSAT_HU" width="576" height="366"></iframe>

Commented code below:
~~~js
//CLASSES
//Using classes

//Instead of having to create a variety of functions for an object each time, using classes will form a template/blueprint for that object, organising the code in a more concise way as the overall code becomes more complex. This allows me to categorise different objects/change various functions of that object in their own blueprint without affecting other objects within the code.

//2. To do this I am going to define my variable as flower again 

let circle; //declared variable 'circle'


function setup() { //called once
  createCanvas(576, 324); //creating canvas
                         //576 pixels wide 
                         //324 pixels tall 
  
circle = new Circle(); //giving variable a value, representative of a class ('new' + name of class() is used to declare a class ) 
}

function draw() { //loops
  background('red'); //background is red
  circle.display(); //class's function
  circle.hover(); //class's function
}
//4. This is our class. In order to put values to define what the flower is, or what data/functionality it holds, I have to utilise constructor(), this operation is kind of similar to the way function setup() works. 

class Circle { //class name (as defined in setup)
  constructor(){ //constructor acts as the class' own version of setup
    
//When I am putting data into the constructor, I need to actually declare the variable just like how I declare variables normally if I want to attach a value to it. Instead of let though, I have to use 'this'. 
    this.x = 300; //value on the x axis is 300 pixels.
    this.y = 150; //value on the y axis is 150 pixels.
  }
//REMEMBER, you have to declare it again, so always use this in your class
  hover() { //the class' custom function name 'hover' (I can treat this as the class' own version of function draw)
    this.x = this.x + random(-1, 1); //the declared variable is 300 pixels on the x axis + moves in whatever direction '-1' pixel left and '1' pixel right. 
    this.y = this.y + random(-1, 1); //the declared variable is 300 pixels on the y axis + moves in whatever direction '-1' pixel left and '1' pixel right. 
  }

  display() { //function name 'display'
    noStroke() //no black outline
    fill(255); //fill circle white
    ellipse(this.x, this.y, 40);  //draw circle, with x and y position being the variable values declared in constructor, and a size of 40 pixels.    
   }
}

//Now if you go back up to the function draw section, I can now call upon flower to hover, and display, utilising the declared variable I gave the class and whatever function.
~~~


