---
layout: post
title:  "Audio Visualisers"
date:   2022-09-22 14:43:10 +1000
categories: jekyll update
---

In this post, I wanted to experiment purely on combining creative coding with the emphasised use of audio and came across the performative notion of audio visualisers. When researching the linkage between audio performance and code, I came across the use of a [fast fourier transform]( https://p5js.org/reference/#/p5.FFT) algorithm that analyses individual audio frequencies of sound or music within a waveform. 

# Audio Visualiser Experiment 1

In the first experiment, I focused on mapping a song and its audio frequencies to a line that went across the window’s canvas. The way the mapped waveform moves according to the song’s amplitude was satisfying to watch. In this case, I focused purely on the amplitude of the song (the relative strength of sound waves (transmitted vibrations)) utilising a fft.waveform() when mapping the waveform particles. 

This experiment was completed through the aid of tutorials in the [p5js library]( https://p5js.org/reference/#/p5.FFT) and the [coding train]( https://youtu.be/2O3nm0Nvbi4)

<iframe src="https://editor.p5js.org/vivianluh/full/AKuTEAARv" width="700" height="542"></iframe>

Commented code below:

~~~js
let song; //declare global variable 'song'
let fft; //declare global variable 'fft' (fast fourier transform)

function preload(){ //loads before setup
  song = loadSound('we lost the summer.mp3') //load song
}

function setup() { //runs once
  createCanvas(800, 600);//create a cavnas 
                                           //width size of particular window
                                           //height size of particular 
  
  fft = new p5.FFT() //fast fourier transform 
                     //every frame, the fft object will analyse the sound
                     //at that exact point in time 
                     //and return an array of values

}

function draw() {
  background(255);
  stroke('rgb(0,192,255)')
  // fill('rgb(0,192,255)')
  strokeWeight(4) 
  
  let wave = fft.waveform()//this is where we store the waveform data
  
  
  beginShape() //function that make waveform particles more connected to a line
  //create for loop to loop this waveform data to draw it across canvas
  //the for loop iterates from 0 to the width of the canvas
  //this allows us to put a point from the wave on each x point across the whole screen
  for (let i = 0; i < width; i = i + 1)
    {
      
      //maps the for loop variable to the index of the wave that we want
      //the value of the index must be an integer so we floor() it
      let index = floor(map(i, 0, width, 0, wave.length))
      
     
      let x = i  //x point is equal to the foor loop variable 
      //y point is equal to the waveform value that is placed at the current index 
      //we need to scale it up to actually see the waveform movements 
      //default its between -1 and 1
      //scale it up to 300 to see its movements
      //offset wave to the middle of the window
      let y = wave[index] * 300 + 600 / 2
      
      vertex(x, y)//used for beginShape and endShape functions 
                  //specify the coordinates when constructing line
      
    }
  endShape()//function that makes waveform particles more connected to a line
}

function mousePressed(){ //when mouse is pressed
  if (song.isPlaying()) //if the song is playing when mouse is pressed
  {
    song.pause() //pause the song
    noLoop() //the waveform movement will pause too
  }
  
  else //otherwise when mouse is pressed again
  {
    song.play() //continue playing song
    loop() //continue the loop for the waveform
  }
}
~~~

# Audio Visualiser Experiment 2

In the second, I wanted to achieve something a bit more complicated, as viewed in many of the audio visualisers on youtube/the internet. A [tutorial]( https://youtu.be/uk96O7N1Yo0) that I followed helped me unpack fft.analyse() when working with fft. Apart from also mapping the vibrations of the song, this experiment also maps the energy output of the song through the moving particles that are emitted from the circle. This combination of both mapping energy output and transmitted vibrations establishes a wholy representation of the song’s audio movements. 

<iframe src="https://editor.p5js.org/vivianluh/full/q2qKaXeJp" width="800" height="742"></iframe>

Commented code below:

~~~js
let song; //declare variable 'song'
let fft; //declare variable 'fft' (Fast Fourier Transform)
let particles = []; //declare variable 'particles' as an empty array


function preload(){ //loads before setup
  song = loadSound('we lost the summer.mp3')
}

function setup() { //runs once
  createCanvas(800, 700); //create a cavnas 
                                           //width size of particular window
                                           //height size of particular window
  angleMode(DEGREES) //change the mode to degrees
  fft = new p5.FFT() //fast fourier transform 
                     //analysis algorithm
                     //isolates individual audio frequencies within a waveform.
}

function draw() { //runs continuously 
  background(255); //canvas is white
  stroke('rgb(0,192,255)') //stroke is blue
  fill('rgb(0,192,255)') //fill the object blue
  strokeWeight(4) //thickness is 4 pixels
  
  translate(width / 2, height / 2) //object is center of canvas window
  
  fft.analyze() //analyse the energy according to the particles 
  amp = fft.getEnergy(20, 200)
  
  let wave = fft.waveform() //this is where we store the waveform data
  
  beginShape()
  //make for loop of the waveform particles that maps into a circle
  //to do this we can create two waveforms, where one of them is mirrored
  for (let i = 0; i <= 180; i = i + 1)
    {
      //maps the for loop variable to the index of the wave that we want
      //we create a half circle that iterates from (0, 180)
      //180 is number of degrees in half circle
      
      let index = floor(map(i, 0, 180, 0, wave.length -1))
      
      
      //we use the index to map the radius of circle to the waveform
      //last two are the min and max radius of the circle
      let r = map(wave[index], -1, 1, 150, 350)
      
      let x = r * sin(i) //x point maps to r x sin angle
      let y = r * cos(i)//y point maps to r x cos angle
      vertex(x, y)
    }
  endShape()
  
  beginShape()
  //dupiclate another half circle and mirror it
  for (let i = 0; i <= 180; i = i + 1)
    {
      let index = floor(map(i, 0, 180, 0, wave.length -1))
      
      let r = map(wave[index], -1, 1, 150, 350)
      
      let x = r * -sin(i) //mirror it by changing sin angle on x point to a negative
      let y = r * cos(i)
      vertex(x, y)
    }
  endShape()
  
  //make the flying particles
  let p = new Particle(); //create new class variable 'Particle'
  particles.push(p) //push the class 'article' into the empty 'particles' array
  
  //for loop to put array into action
  //instantiate the array 
  for (let i = particles.length - 1; i >= 0; i--)
  {
    if (!particles[i].edges()) //calls the if the particles dont reach edge
    {
      
      particles[i].update(amp > 200); //then call update function of the 'Particle' class
      //amp tracks the output of energy 
      //200 is a good output energy for my song
      particles[i].show() //then call the show function of the 'Particle' class
    }
    else //otherwise 
    {
      particles.splice(i, 1)
        
    }
    
  }
  
}

class Particle { //create the blueprint for the flying particles
  constructor(){ //set up of the class
    this.pos = p5.Vector.random2D().mult(250); //when particle is created
    //place it randomly at the perimeter of the waveform
    //the vector has a length of 1
    //to get it to be placed at the perimeter of the waveform, we multiply it by 250
    //250 is the average of the waveform map (150, 350)
    this.vel = createVector(0, 0); //the velocity will be 0 when first created
    
    this.acc = this.pos.copy().mult(random(0.0001, 0.00001));
    //acc will slowly increase their velocity over time
    //same direction as position vector
    //the acc should be much smaller than than the position vector
    //random will make the movement more organic
    
    
    this.w = random(3, 5);//random width of particles
  }
  
  update(cond){ //in order for the vectors to affect each other properly
    //the acceleration must be added to the velocity
    //the velocity must be added to the position
    this.vel.add(this.acc);
    this.pos.add(this.vel);
    
    if (cond) //add velocity to position a couple more times
    {
      this.pos.add(this.vel);
      this.pos.add(this.vel);
      this.pos.add(this.vel);
    }
  }
  
  edges(){ //remove particles when they reach the boundaries of canvas
    //if particles reach all edges of canvas
    if (this.pos.x < -width /2 || this.pos.x > width /2 || 
       this.pos.y < -height /2 || this.pos.y > height /2) 
      {
        return true //it will be true
      } 
    else { //otherwise it will return false
      return false
    }
  }
  
  
  show(){ //show the particles in an ellipse
    noStroke()
    fill('rgb(0,192,255)') //fill each particles blue
    ellipse(this.pos.x, this.pos.y, this.w) //position is where the waveform is mapped to a circle
  }
}

function mousePressed(){ 
  if (song.isPlaying())//if mouse is pressed while song is playing
  {
    song.pause() //pause song
    noLoop() //stop the for loop
  }
  
  else //otherwise 
  {
    song.play() //play the song
    loop() //play the for loop
  }
}
~~~

