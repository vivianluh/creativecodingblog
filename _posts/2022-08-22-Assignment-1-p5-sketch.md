---
layout: post
title:  "Assignment 1 -p5 sketch banner"
date:   2022-08-22 14:43:10 +1000
categories: jekyll update
---
The ‘RMIT Creative Coding Specialisation’ banner aims to:

-	Present ‘RMIT’ as big and bold, while incorporating colour as a key element in its delivery
-	Present an element that has ‘randomness’ to it and the way it acts seems unpredictable
-	Invite user interactivity through mouse clicking and mouse movement
-	Incorporate all key Javascript concepts introduced over the last few weeks (variables/functions/conditional logic/classes/arrays/iteration)

<iframe src="https://editor.p5js.org/vivianluh/full/C6Gc3xvVO" width="576" height="366"></iframe>

Commented code below:

~~~js
//RMIT CREATIVE CODING BANNER

//GOAL: An interactive 'RMIT Creative Coding Specialisation' banner

//1. Users can move the mouse around to change the look of 'RMIT'. 
//2. Users can also click on the banner to place a randomly moving RMIT logo on the banner
//3. Utilise the 6 javascript concepts 




let LOGO = []; //declared variable 'LOGO' as an empty array
let RMIT; //declared variable 'RMIT' for the big 'RMIT' text
let CCS; //declared variable 'CSS' for the 'creative coding specialisation' text


let symbol; //declared variable 'symbol' for image
let museo; //declared variable 'museo' for font

function preload() //loads before setup()
{
  symbol = loadImage('RMIT.png'); //gave symbol variable a value
  museo = loadFont('fonts/Museo 700.otf') //gave museo variable a value
}


function setup() //runs once, at the beginning
{
  createCanvas(576, 324); //creating canvas
                         //576 pixels wide by
                         //324 pixels tall
  RMIT = new Rmit(); //giving variable 'RMIT' as a class named 'Rmit'
  CSS = new Css();   //giving variable 'CSS' as a class named 'Css'
}


function mousePressed() //runs once when mouse is pressed 
{
  let f = new logo(mouseX, mouseY) //declaring variable 'f' as a class with reference to mouseX, and mouseY of the 'logo' class
  LOGO.push(f); //push is used when the mouse is pressed, the data that just ran will stay present on the screen. 
}


function draw() //loops after setup has run
{
  background('red'); //fills canvas red 
  
  
  //for loop; declaring that variable 'i' is 0
  //I can call the array with 'i'
  //if i is smaller than the logo.length then I can add another logo image everytime I click on the screen
  //___.length is a property used to return the number of elements that an array has. 
  //I cant make it infinite otherwise the browser will crash
  for(let i = 0; i < LOGO.length; i = i + 1) 
  {
    LOGO[i].hover(); //calling the class's 'logo' custom function of hover()
    LOGO[i].display(); //calling the class's 'logo' custom function of display()
  }
  
  RMIT.rmit1(); //calling the class's 'Rmit' custom function of rmit1()
  RMIT.rmit2(); //calling the class's 'Rmit' custom function rmit2()
  RMIT.rmit3(); //calling the class's 'Rmit' custom function rmit3()
  
  CSS.display(); //calling the class' 'Css' custom function of display()
}


class Css //name of class for 'Creative Coding Specialisation' text that I declared in setup() 
{
  constructor() //acts as the class own version of setup() where I declare variables. I have to declare variables with 'this.' (class's version of 'let')
  {
    this.col_1 = color(0, 0, 84); //declaring variable 'col_1' as dark blue
    this.x = 50 //declared variable 'x' as 50 pixels
    this.y = 260 //declared variable 'y' as 260 pixels

  }
  
  display() //custom function 'display' to display text
  {
    fill(this.col_1) //fill text dark blue
    textFont(museo) //make text the 'museo' font declared in preload
    textSize(32) //size of text is 32 pixels
    
    //write Creative Coding Specialisation 
    //positioned at 50 pixels on the x axis 
    //positioned at 260 pixels on the y axis
    text('Creative Coding Specialisation', this.x, this.y)
  }
}




class logo //name of class for RMIT logo that I declared in setup(). The goal is to make the logo jitter/hover around screen randomly.
{
  constructor(x, y) //defined constructor with parameters x and y
  {
    this.x = x; //declaring variable x as x
    this.y = y; //declaring variable y as y
  }

  hover()  //custom function 'hover'
  {
    //declare variable x with the value that;
    //x position will move randomly between 2 and -2 on x axis
    //y position will move randomly between 2 and -2 on y axis
    this.x = this.x + random(2,-2); 
    this.y = this.y + random(2,-2);
  }
  
  display() //custom function 'display'
  {
    image(symbol, this.x, this.y) //display the image declared as 'symbol' with the x and y value defined in constructor   
   }
}



class Rmit { //name of class for 'RMIT' text that I declared in setup(). Goal is to use conditional logic here
  
  constructor()//setup
  {
    this.col_1 = color (0, 0, 84); //declared variable 'col_1' as dark blue
    this.col_2 = color ('#03A9F4'); //declared variable 'col_2' as blue
    this.col_3 = color (250, 200, 0); //declared variable 'col_3' as yellow
    this.y = 210 //declared variable 'y' as 210 pixels, to be used for y axis position
    this.size = 200 //declared variable 'size' as 200 pixels, to be used for text size
  }
  
  rmit1() //custom function 'rmit1' - to be displayed without conditional logic
  {
    fill (this.col_1) //fill text dark blue
    textFont (museo) //make text the 'museo' font declared in preload
    textSize(this.size) //size is 200 pixels
    text('RMIT', 50, this.y) //write 'RMIT', 50 pixels on x axis, 210 on y axis
    
  }
  
  rmit2() //custom function 'rmit2' - conditional logic
  {
     if (mouseX > 50) //true statement if mouse position is bigger than 50 pixels on the x axis, then the following will happen;
     {
       fill (this.col_2) //fill text blue
       textFont (museo) //make text the 'museo' font declared in preload
       textSize (this.size) //size is 200 pixels
       text('RMIT', 40, this.y) //write another 'RMIT' that is positioned 10 pixels to the left of rmit1 and on the same y axis
     }
  }
  
  rmit3()
  {
    if (mouseX > 300) //true statement if mouse position is bigger than 300 pixels on the x axis, then the following will happen;
    {
      fill (this.col_3) //fill text yellow
      textFont (museo) //make text the 'museo' font declared in preload
      textSize (this.size) //size is 200 pixels
      text ('RMIT', 30, this.y) //write another 'RMIT' that is positioned another 10 pixels to the left from rmit2 and on the same y axis. 
    }
  }
  
}

~~~
