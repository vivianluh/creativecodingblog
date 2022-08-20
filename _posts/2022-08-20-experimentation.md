---
layout: post
title:  "p5 Experimentation"
date:   2022-08-20 14:43:10 +1000
categories: jekyll update
---
In this section, I aim to apply a combination of Javascript concepts (variables, iteration, conditional logic, custom functions, arrays, classes) in small experimental p5 sketches. Hopefully, the knowledge gained from these exercises will combine to aid in creating the final ‘RMIT Creative Coding Specialisation’ banner design. Working in smaller experimental sections will also aid in troubleshooting any coding issues that I come across, and therefore will not jeopardise my final written p5 sketch for my banner.

# Experiment - Conditional Logic 

In this exercise, I worked with font and colour together when applying conditional logic. While applying this concept, I also introduced several Javascript concepts such as declaring variables, and giving it values, and establishing custom functions to organise my p5 sketch.

<iframe src="https://editor.p5js.org/vivianluh/full/SNEcCOr6c" width="576" height="366"></iframe>

Commented code below:

~~~
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

<iframe src="https://editor.p5js.org/vivianluh/full/HExdWXcCg" width="700" height="700"></iframe>



Commented code below:

~~~
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

<iframe src="https://editor.p5js.org/vivianluh/full/kL3TM4kGN" width="700" height="700"></iframe>

Commented code below:
~~~
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
