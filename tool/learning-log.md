# Tool Learning Log

Tool: **Making a game from scratch (javascript, css, html)**

Project: **My main project idea is making a food rpg game where the player can cook different food to earn levels to defeat monsters in the cave.**

---

10/23/23:
* Link: https://www.youtube.com/watch?v=fyi4vfbKEeo&list=PLcjhmZ8oLT0r9dSiIK6RB_PuBWlG1KSq_ 

#### Getting Started (Day1)
* `<canvas class = "game-canvas" width="352" height="198">` --> helps create how big you want the background and canvas to be 

`overflow: hidden;`
* In the code below, it helps create a box (the box will be how big we want the game to be)
```JS
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
* How to load an Image into a canvas 
```JS
//Javascript
init() {
    const image = new Image(); // helps create a new image 
    image.onload = () => { // helps load the image 
        //this.ctx.drawImage(image, x, y) 
    };
    image.src = "link to the image"; // helps store the image inside the new image 
}
```
* One challenge I had was when I was creating the image. When I created the image, I was confused what is `ctx`. 
`this.ctx.drawImage(image, x, y)`
However, then I realized that `ctx` was a place to store all the drawing method, so that when we want to use the drawing method, you can use `this.ctx`.
```JS
this.ctx = this.canvas.getContext("2d");
```
**Questions**

* Something I am going to try next is 

10/27/23:
* Link: https://www.youtube.com/watch?v=fyi4vfbKEeo&list=PLcjhmZ8oLT0r9dSiIK6RB_PuBWlG1KSq_ 

#### Getting Started (Day 2)




<!-- 
* Links you used today (websites, videos, etc)
* Things you tried, progress you made, etc
* Challenges, a-ha moments, etc
* Questions you still have
* What you're going to try next
-->
