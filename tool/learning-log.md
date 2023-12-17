# Tool Learning Log

Tool: **Making a game from scratch (javascript, css, html)**

Project: **My main project idea is making a food rpg game where the player can cook different food to earn levels to defeat monsters in the cave.**

---

**10/23/23**:
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

**10/27/23 - 10/30/23**:
* Link: https://www.youtube.com/watch?v=fyi4vfbKEeo&list=PLcjhmZ8oLT0r9dSiIK6RB_PuBWlG1KSq_
#### Getting Started (Day 2)
**IMPORTANT**: **ORDER MATTERS WHEN PLACING IMAGES**
* PUT IMAGES YOU WANT AS BACKGROUND **FIRST**, THEN THE OTHER SPRITES
* Today I learned about how to place the images on the canvas
```Javascript
// Configure Animation and Initial State
this.animations = config.animations || {
    idleDown: [
        [0,0]
    ]
}
this.currentAnimation = config.currentAnimation || "idleDown";
this.currentAnimationFrame = 0;

// Position of the sprite
const x = this.gameObject.x * 16 - 8;
const y = this.gameObject.y * 16 - 8;

// Helps show only one sprite in a sprite sheet
ctx.drawImage(this.image,
0, 0,
32, 32,
x, y,
32, 32,
)
```
In the code above, I was really confused with `this()` because I wasn't really sure which method `this()` is referring to. In addition, I tried rewatching the tutorial and found out that `this()` is referring to the previous method that you created inside of the method.

**11/6/23 - 11/13/23**:
* Link: https://www.youtube.com/watch?v=fyi4vfbKEeo&list=PLcjhmZ8oLT0r9dSiIK6RB_PuBWlG1KSq_
#### Getting Started (Day 3)
* Today I learned about placing game objects. Game objects are different sprites in the game.
```Javascript
 const cupcake = new GameObject({
    x: 7,
    y: 10,
})
const menu = new GameObject({
    x: 7,
    y: 9,
})
```
* When creating a game object ,**YOU NEED TO CREATE A NEW GAME OBJECT FOR EVERY SPRITE** using `const spriteName = new GameObject({})`.
* Something that I am going to try next is making the sprite move.

**11/20/23 - 11/27/23**:
* Link: https://www.youtube.com/watch?v=fyi4vfbKEeo&list=PLcjhmZ8oLT0r9dSiIK6RB_PuBWlG1KSq_
#### Getting Started (Day 4)
* Today I learned about how to make the sprite move through creating different position for the sprite
```Javascript
draw(ctx) {
const x = this.game0bject.x * 16 - 8;
const y = this.game0bject.y * 16 - 18;
this.isLoaded && ctx.drawImage(this.image,
0,0,
32,32,
x, y,
32,32
)}
```
In the code above, it grabs the sprite position using `this.gameObject.x` and loading it to the `ctx.drawImage`, so that when you run the code, it only show one sprite moving around the canvas.

**12/4/2023**
* Link: https://www.youtube.com/watch?v=fyi4vfbKEeo&list=PLcjhmZ8oLT0r9dSiIK6RB_PuBWlG1KSq_
#### Loops (Day 5)
Today I learned about how to make a loop, where it helps load all objects and sprite in the game
```JS
startGameLoop() {
    const step = () => {
        console.log("Stepping!");
        requestAnimationFrame() => {
            step();
        })
      }
      step();
    }
```
`requestAnimationFrame() => {}` --> `requestAnimationFrame()` helps grab the objects and sprite and making it step. In the beginning, I tried putting the step in different places to see what will happen. I learned that if you put `step()` before the `requestAnimationFrame()`, it can cause a infinite loop, causing the computer to froze.
```JS
startGameLoop() {
    const step = () => {
          step();
        requestAnimationFrame() => {

        })
      }
      step();
    }
```
In addition, I learned that if you put `step()` after or inside the `requestAnimationFrame()`, it will not cause a infinite loop.
**IMPORTANT:** To prevent a infinite loop from happening, we put code we want to run **INSIDE** or **AFTER** **requestAnimationFrame()**

* These few weeks, I made a canvas for how big I wanted the game to be. In addition, after I finish making the canvas for my game, I started putting objects, sprites, and background on my canvas. Lastly, I started making loops to make the object appear forever as well as making the movements move constantly when you click on the mouse.

<!--
* Links you used today (websites, videos, etc)
* Things you tried, progress you made, etc
* Challenges, a-ha moments, etc
* Questions you still have
* What you're going to try next
-->
