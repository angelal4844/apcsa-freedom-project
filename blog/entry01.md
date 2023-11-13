# Entry 1 (Deciding on my tool and start tinkering with my tool)
##### 11/13/23

### Context 
These few weeks, I was deciding on what my freedom project will be about and what my tool will be. In addition, I started tinkering with my tool as well as planning how I want my game to look like. 

### TOOL 
The tool I am choosing is **making a game from scratch (javascript,html, and css (no library))**. During the summer, I was finding different links and websites to create a game when I come across this Youtube tutorial, where we can learn about how to make a game from scratch. I was following the tutorial on how to make a rpg pizza game called "Pizza Lengends." Through this tutorial, I found my passion of using this tool to make my freedom project. 


These few weeks, I started to learn how to create a canvas for the game as well as how to load a image into the canvas. In the tutorial, I learned that to create a canvas, you use `<canvas class = "game-canvas" width="352" height="198">`. In addition, I also learned that to create a box inside of a canvas you need to use
```Java 
// html
.game-container{
    position: relative;
    width: 352px; 
    height: 198px; 
    margin: 0 auto; 
    margin-top: 20px;
    outline: 1px solid #fff; 
}
```
When watching the tutorial, I also learned that to load an image, you need to use `image.onload = () => {}`.
```Java 
//Javascript
init() {
    const image = new Image(); // helps create a new image 
    image.onload = () => { // helps load the image 
        //this.ctx.drawImage(image, x, y) 
    };
    image.src = "link to the image"; // helps store the image inside the new image 
}
```
After I learned the code, I tried tinkering with the code by myself to see if the tool I learned is something I would want to use for my freedom project. First, I tried creating a file for html, css, and javascript. Then, I created a canvas using `<canvas class = "game-canvas" width="300" height="200">` and add another box inside the canvas. In addition, I also tried loading a ice cream picture inside the canvas. When I run the code, I could see the picture inside the box. 
```Java 
<canvas class = "game-canvas" width="300" height="200">


// html
.game-container{
    position: relative;
    width: 300px; 
    height: 200px; 
    margin: 0 auto; 
    margin-top: 20px;
    outline: 1px solid #fff; 
}

//Javascript
init() {
    const image = new Image(); 
    image.onload = () => {
        this.ctx.drawImage(image, 150,150);
    };
    image.src = "images/ice-cream.png";
}
```

### PROJECT IDEA AND PLANNING 
In the beginning, I was deciding what my freedom project idea will be. Until, I got my inspiration when I was eating hotpot with my family. I was wondering why not make a rpg food game, where the player can create different foods as well as leveling up through collecting different ingredients in the cave to help unlock new food. These few weeks, I started to plan out the canvas for my game. I started to plan how many boxes I want inside the canvas and the shape of the canvas. 

### SKILLS
Some skills I learned is problem decomposition and how to learn. Through my journey in tinkering, I learned problem decomposition by breaking up the topics and learning one topic every day. In addition, I also learned how to learn by watching the tutorial first and then tinkering it on my own to make sure that I understand how to do it. 

### EDP
I am in stage 1, define the problem and stage 2, research the problem. These few weeks I was planning and deciding what my freedom project is and the tool I wanted to use. I decided to create a food rpg game, where the user can create food and fight monsters in the cave to level up and unlock new food. In addition, I also started with tinkering with my tool and learned how to load an image on a canvas and how to create a canvas. Next blog, I would continue tinkering with my tool through watching different tutorials. 

### Links I used 
[Link to the tutorial]( https://www.youtube.com/watch?v=fyi4vfbKEeo&list=PLcjhmZ8oLT0r9dSiIK6RB_PuBWlG1KSq_)

[Next](entry02.md)

[Home](../README.md)