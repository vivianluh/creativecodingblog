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

<iframe src="https://editor.p5js.org/vivianluh/full/AKuTEAARv" width="800" height="642"></iframe>

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

<iframe src="https://editor.p5js.org/vivianluh/full/q2qKaXeJp" width="1200" height="842"></iframe>


