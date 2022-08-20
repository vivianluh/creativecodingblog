---
layout: post
title:  "p5 Experimentation"
date:   2022-08-20 14:43:10 +1000
categories: jekyll update
---
In this section, I aim to apply a combination of Javascript concepts (variables, iteration, conditional logic, custom functions, arrays, classes) in small experimental p5 sketches that will hopeful gradually combine to create the final ‘RMIT Creative Coding Specialisation’ banner design. Working in smaller experimental sections will also aid in troubleshooting any coding issues that will not jeopardise the entirety of my code. 

# Experiment 1 - Conditional Logic 

In this exercise, I worked with font and colour together when applying conditional logic. While applying this concept, I also introduced several Javascript concepts such as declaring variables, and giving it values, and establishing custom functions to organise my p5 sketch.

<iframe src="https://editor.p5js.org/vivianluh/full/SNEcCOr6c" width="700" height="700"></iframe>

Commented code below:

`//Conditional Logic`
`//In this exercise I experimented with`
`//conditional logic, applying the expression '>' as a relational operation`
`//defining variables`
`//creating custom functions and calling them`

`let museo //declare variable 'museo' (which is font name)`

`let col_1, col_2, col_3, col_4 //declare variable names for the colours`

`function preload () //load the font 'museo', getting it ready before function setup as it is an external file`
`{`
 ` museo = loadFont ('fonts/Museo 700.otf')`
`}`


`function setup () //runs once, at the beginning`
`{`
 ` createCanvas (576, 324) //created canvas`
                        `  //576 pixels wide `
                         ` //324 pixels tall `
  
  `col_1 = color (0, 0, 84) //gave variable a value colour of blue`
  `col_2 = color (230, 30, 42)//variable value colour of red`
  `col_3 = color (250, 200, 0)//variable value colour of yellow`
  `col_4 = color ('#FF5722')//variable value colour of orange`
`}`

`function draw () //loops forever after setup has run in the beginning`
`{`
  `background(col_1)//fill canvas blue`
  `rmit1(); //call custom function stated in rmit1`
  `rmit2(); //call custom function stated in rmit2`
  `rmit3(); //call custom function stated in rmit3`
`}`

`function rmit1(){`
 `fill (col_2)//make text red`
  `textFont (museo)//utilised defined variable`
  `textSize (200)//text size is 200 pixels`
  `text (`RMIT`, 50, 240)//place RMIT, on x value 50, y value 240`
}


`function rmit2() //defined a custom function`
`{`
  `//conditional logic statement if mouse along the x axis reaches more than 300 pixels then;`
  `if (mouseX > 300){`
`fill (col_4) //make text orange`
  `textFont (museo)`
  `textSize (200)`
  `text (`RMIT`, 40, 240) //place another RMIT text, 10 pixels to the left of the rmit1 text. `
  `}`
`}`
  


`function rmit3() //defined a custom function`
`{`
  
`//conditional logic statement if mouse along the x axis reaches more than 300 pixels then;`
`if (mouseX > 300){ `
`fill (col_3) //make text yellow`
  `textFont (museo)`
  `textSize (200)`
  `text (`RMIT`, 30, 240) //place yet another RMIT text, another 10 pixels to the left of rmit2.`
  `}`
`}`

