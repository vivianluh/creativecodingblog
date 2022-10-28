---
layout: post
title:  "Justin's Digital Room"
date:   2022-10-27 14:43:10 +1000
categories: jekyll update
---

The final assignment of my creative coding journey aims to share with my peers a personal side of my life, my community, my skills, and the people who mean a lot to me in my life. I believe this assignment was extremely rewarding as I was able to combine all my coding skills I have developed over the semester and more importantly, share it with someone who means a great deal to me. 

My final creative coding project is named "Justin's Digital Room" which presents a simple interactive and animated artwork that showcases a cartooned version of my brother - Justin, working at his desk tonight. As he lives in Sydney, I hope to connect with him in the form of code and create a coded environment which captures his interests, hobbies, skills, and personality while also hopefully forming a sense of nostalgia, as if he was transported back home to his room back in Melbourne. 

# Justin's Digital Room 

[Visit](http://digitalmedia.rmit.edu.au/~s3900746/JustinsRoomIsSmelly/) Justin's Room yourself :)
Also make sure to check out my brother's [reaction](https://youtu.be/FkZgnrs9KtQ) to seeing his digital room :)

![Imgur](https://i.imgur.com/Nce23Dv.jpg)

![Imgur](https://i.imgur.com/LvK8hg7.jpg)

![Imgur](https://i.imgur.com/ByMr2vt.jpg)

To create this digital room and combine all assets together I utilised html, css, and javascript. I thought the use of these coding languages was suitable because I wanted to deploy a website that could be easily accessible on all browsers and this would allow Justin to access it wherever and whenever. The combination of these coding languages would also be suitable to play my animations smoothly on all browsers. 

# What I learnt?

The process of combining different languages together (HTML, CSS, Javascript) was something that felt overwhelming to me at first, however after getting the hang of properly linking all working pages together, I was able to see how this process was extremely rewarding at the end. 

# What was interesting?

Having the opportunity to combine both a variety of coding languages together as well as external sources but also utilising my skills outside of the coding world and utilise it to my advantage into code was something extremely interesting to unpack and strengthen. In this project, I was able to combine my illustration/animating skills with code to create an experience and project that felt whole. The opportunities that code allows are extremely expansive and open and I guess the next step for me regarding my final project, I would love to deploy 'Justin's Digital World' as a chrome extension utilising code for which my brother can further personalise his chrome browser. 

# What left an impression?

Being able to create something really personalised for someone else made the entire process and my journey in code extremely worthwhile and super special. At the end of the day, being able to design and create a piece of work for someone and establish a positive and genuine connection to strengthen a relationship is something that means the world to me. :)


# Code - HTML Foyer page
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Roboto+Mono:wght@300;400;500;700&display=swap" rel="stylesheet">

    <!-- link to the stylesheet
    something to note which was a problem I encounted when deploying the website 
    in the index.html (the root), when linking you dont need to use '/', just link it as it is named in the root folder -->
    
    <link rel="stylesheet" href="style.css">  
    <!-- IDEA: create a page that acts like a foyer that doesn't immediately show a reveal until clicking to enter -->
    <title>Justin's Foyer</title>
</head>


<body>
    <section class="foyer"> <!-- create a section class to easily manipulate different elements in CSS -->
        <!-- I am confident using sections and divs instead of utilising body/header to divide elements -->
        <h1>HELLO FAMMUS! WELCOME TO YOUR DIGITAL ROOM * 
            HOVER OVER THE LIGHT SWITCH (THE SQUARE) 
            TO START OR STOP DOING WORK
        </h1>
        <!-- link the text 'click here to enter' which will link to the page that has the interactive artwork -->
        <a href="pages/justinsroom.html"><p>CLICK HERE TO ENTER</p></a>
    </section>
</body>
</html>
```

# Code - HTML Justin's Digital Room

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <!--fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Roboto+Mono:wght@300;400;500;700&display=swap" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Comfortaa:wght@700&display=swap" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Barlow+Condensed:wght@400&family=Comfortaa:wght@400&display=swap" rel="stylesheet">
    
    <!-- link to stylesheet -->
    <!-- something important to note is that in pages that are in folders from the root, linking it is different -->
    <!-- when linking outside of root, utilise ../ -->
    <link rel="stylesheet" href="../style/justinsroom.css">
    
    <title>Justin's room is very smelly</title>
</head>

<body>
    <!--clock called from javascript-->
    <div id="MyClockDisplay" class="clock" onload="showTime()"></div>

    <!--animations -->

    <!-- lightswitch -->
    <div class="relax">
        <div class="square"></div>
    </div>
    <!-- the images that make up the work -->
    <div class="images"></div>
    
    <!--javascript for the clock -->
    <!-- link to the javascript -->
    <script src="../java/app.js"></script>
</body>
</html>
```

# Code - CSS Foyer Room

```
*{
    margin: 0;
    padding: 0;
}


.foyer{
    height: 100vh;
    background-color: rgb(5, 0, 106);
}

.foyer h1{
    font-family: 'Roboto Mono', monospace;
    text-align: center;
    color: white;
    position: absolute;
    top: 48%;
    left: 50%;
    transform: translate(-50%, -50%);
    font-size: 30px;

}


.foyer p{
    font-family: 'Roboto Mono', monospace;
    text-align: center;
    color: white;
    position: absolute;
    top: 62%;
    left: 50%;
    transform: translate(-50%, -50%);
    font-size: 15px;
}
```

# Code - CSS Justin's Digital Room

```

*{
    margin: 0; /* There is no space between the inner box */
    padding: 0; /*  and the outer box */
}

/* styling the clock display */
.clock {
    position: absolute; /* position absolute means the element is plucked out of the document, I can put it anywhere I want */
    top: 5%; /* 5% of the window from the top */
    left: 7%; /* 7% to the right of the window from the left */
    transform: translateX(-50%) translateY(-50%); /* moves elemtn from current position according to x and y parameters */
    color: #2953c8; /* colour text blue */
    font-size: 3.0vh; /* font size adjusts according to the viewport size */
    font-family: 'Barlow Condensed', sans-serif; /* defined a particular font */
    letter-spacing: 5px; /* spaces letters */
    z-index: 0; 
}

/* creating the moving work utilising background-image */
/* background-image was utilised so it would fill up the space of the viewport and adjust according to 
the size of the vh when it is to be manipulated */
.images{

    /* calling images in hierarchy */
    background-image: 
    url("../img/switch.png"),
    url("../img/bed.png"),
    url("../img/lights.png"),
    url("../img/fan.png"),
    url("../img/neonsign.png"),
    url("../img/justinoff.png"),
    url("../img/Computer2.png"),
    url("../img/bg.png");
    background-size: cover; /* cover vh */
    background-repeat: no-repeat; /* fill vh */
    height: 100vh; /* the whole vh is considered */
}

/* css hover function is utilised */
/* when mouse hovers, things start to animate */
/* utilises gifs to create moving images */
.images:hover{
    background-image:
    url("../animations/switch.gif"),
    url("../img/bed.png"),
    url("../animations/lights.gif"),
    url("../animations/neonsign.gif"),
    url("../animations/neonsign.gif"), 
    url("../img/justin.png"),
    url("../animations/Computer2.gif"),
    url("../img/bg.png");

}

/* styling the lightwitch display */
/* using absolute to place it wherever */
/* making sure height and width change corresponding to vh */
/* when mouse hovers, the colour changes from on (yellow) to off (blue) */
.relax{
    position: absolute;
    padding-left: 2%;
    padding-top: 33%;
}
.square{
    height: 5.0vh;
    width: 5.0vh;
    background-color: rgb(255, 162, 0);
}

.square:hover{
    background-color: rgb(25, 0, 255);
}
```


# Code - JavaScript Justin's Digital Room
```
function showTime(){ //execute the showTime function
    //this function retrieves the current time on your computer and displays it in the browser

    var date = new Date(); //this creates a date object with the current date and time
    var h = date.getHours(); // 0 - 23 //returns the hour according to the local time 
    var m = date.getMinutes(); // 0 - 59 //returns the minutes according to the local time 
    var s = date.getSeconds(); // 0 - 59 //returns the seconds according to the local time 
    var session = "AM"; //create variable of 'am'
    
    //conditional statement if the hour is from 0 to 12 returns true, nothing happens/use AM
    if(h == 0){
        h = 12;
    }
    
    //if the hour is less than 12 where the hour is in the PM essentially (h - 12 in the pm as there are 24 hours, use PM)
    if(h > 12){
        h = h - 12;
        session = "PM";
    }
    
    h = (h < 10) ? "0" + h : h; 
    m = (m < 10) ? "0" + m : m;
    s = (s < 10) ? "0" + s : s;
    
    var time = h + ":" + m + ":" + s + " " + session;
    document.getElementById("MyClockDisplay").innerText = time;
    document.getElementById("MyClockDisplay").textContent = time;
    
    setTimeout(showTime, 1000);
    
  }
  
  showTime();
```




