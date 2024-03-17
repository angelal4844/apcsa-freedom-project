# Entry 4
##### 3/18/2024

### Context
These few weeks, I continued building my MVP for my game. Last blog, I started planning what my game will look like and the sprites, background, and food that will be included in the game. This few weeks, I drew out all my backgrounds, sprites, and food and stored it into an image folder. In addition, for my MVP, I made a clickable map, where the user can choose the map they want and making the sprites move. During my process in creating my MVP, I faced many challenges and aha moments.
### MVP
#### Clickable Map
When I was creating the clickable map, I first added all the images using `<img src ="image link">` and made all the map the same size and position.
```html
<!-- html -->
 <div class = "game-container">
       <img class = "game-canvas blue" id ="map1" src = "img/sep-room.png">
       <img class = "game-canvas purple" id ="map2" src = "img/kitchen.png">
       <img class = "game-canvas green" id ="map3" src = "img/testRoom.png">
</div>
```

```html
<!-- css -->
<style>
 .blue{
    box-sizing: border-box;
    width: 1000px;
    height: 600px;
    }

.purple{
    box-sizing: border-box;
    position: absolute;
    width: 1000px;
    height: 600px;
    top: 0%;
    left: 0%
    }

.green{
    box-sizing: border-box;
    position: absolute;
    width: 1000px;
    height: 600px;
    top: 0%;
    left: 0%
    }
 </style>
```
After, I finished adding all the images and changing all the images to the same size and position, I started to make each map clickable using javascript.
* First, I started by planning out what will happen when one map is click. When one map is click, the second map will appear, while the other two map will disappear.
* After I finish planning, I started to make each map clickable using `.addEventListener("click", myFunction);`.
```JS
document.getElementById("map1").addEventListener("click", myFunction);
document.getElementById("map2").addEventListener("click", myFunction2);
document.getElementById("map3").addEventListener("click", myFunction3);
```
* In the code above, the code will grab the id of each image and make each image clickable when the user clicks on the image.
* In addition, after I added  `.addEventListener("click", myFunction);` to all the images, I created three different function, so that when the user clicks on the image, the `.addEventListener("click", myFunction);` will know that the user clicks on the image and the function called `myFunction` will run.

* In `myFunction`, I wanted to make the second map appear, while the the first map and the third map will disappear, so that when the first map is clicked, the second map will appear. In the function, I used  `document.getElementById("myBtn").style.visibility= "hidden";`, and `document.getElementById("myBtn2").style.visibility= "visible";` to make the map appear and disappear.
```JS
function myFunction(){
    document.getElementById("map1").style.visibility= "hidden";
    document.getElementById("map2").style.visibility= "visible";
    document.getElementById("map3").style.visibility= "hidden";
}
```
* In the code above, I made map 1 and map 3 disappear using the key word `hidden` and made map 2 appear using the key word `visible`.
* Moreover, for `myFunction2` and `myFunction3`, I made the next map that will be shown appear, while the other map will disappear.
When I run the code using http-server, it worked!
### Making the sprites move
* When making the sprites move, I first started by adding all the sprites using `<img  class = "game-canvas size "src = "img/sprite-1.png">` in html.
```html
 <img  id="num1" class = "game-canvas size position1" src = "img/sprite-1.png">
 <img  id="num1" class = "game-canvas size position2" src = "img/sprite-2.png">
 <img  id="num1" class = "game-canvas size position3" src = "img/sprite-3.png">
 <img  id="num1" class = "game-canvas size position4" src = "img/sprite-4.png">
 <img  id="num1" class = "game-canvas size position5" src = "img/sprite-5.png">
```
* Then, I grab the id of each sprite and make all the sprite be able to move around using`.addEventListener("keydown", e => {});`
```JS
document.getElementById("num1").addEventListener("keydown", e => {
                if(key == "ArrowLeft") {
                    left+= -5

                } else if(key == "ArrowRight") {
                    right+= 5

                } else if (keyCode === DOWN_ARROW) {
                    down += 5

                } else if (keyCode === UP_ARROW) {
                    up+= -5
                }
    });
```
* Inside`.addEventListener("keydown", e => {});`, I made each key equal to the up, down, left, and right key, so that when the user click on the key, the sprite will move in the direction that the user click.

### Challenges and aha moments
* One challenge I faced was when I was making the sprite move. In the beginning, I grab the id of each sprite using `document.getElementById("num1")` and made the sprite move using `.addEventListener("keydown", e => {});`
```JS
document.getElementById("num1").addEventListener("keydown", e => {
    "ArrowUp": "up",
    "ArrowDown": "down",
    "ArrowLeft": "left",
    "ArrowRight": "right",
});
```
However, when I inspect it using `http-server`, it wasn't working. In addition, I looked through my notes and watched the tutorial again and realized that we need to create a if statement because in the code above, the function is only declaring `ArrowUp` to `up` but it is not calling `"ArrowUp": "up",`.

* One aha moment I learned when I was building my MVP was making the map appear and disappear. I learned that when you want a image to disappear, you use `document.getElementById("myBtn").style.visibility= "hidden";`, while when you want a image to appear, you use `document.getElementById("myBtn").style.visibility= "visible";`.

### Skills
* Some skills I learned when working on my MVP is creativity, debugging, and time management. These few weeks, I drew out all the maps and sprites for my game and planned out where each sprite and map will be located in my game. In addition, I also learned time management through organizing my time and planning out what I need to work on everyday.  Moreover, when I was building my MVP, there were errors when I was working on making the sprite move and making the map clickable. However, through tinkering and looking at different websites, tutorials, and my notes, I learned new things through the challenges and aha moments when I was tinkering. 
### EDP
* Last blog, I am on stage 2, research the problem, and stage 3, brainstorm possible solutions. This blog, I am currently on stage 4, plan the most promising solution and stage 5, create a prototype. These few weeks, I drew and planned the sprite and maps I am going to use for my game. In addition, I started planning what I am going to build for my MVP. Moreover, during my process in building the MVP, I made a clickable map and made the sprite move. Next blog, I would continue building my MVP and add new sprites in the game.

[Previous](entry03.md) | [Next](entry05.md)

[Home](../README.md)