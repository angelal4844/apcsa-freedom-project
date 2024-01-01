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
## **Winter Break (12/25/2023 - 1/1/2023)**
* Link: https://www.youtube.com/watch?v=fyi4vfbKEeo&list=PLcjhmZ8oLT0r9dSiIK6RB_PuBWlG1KSq_
#### Maps
* Today I learned about how to create the appearance of the map and how to add game objects inside the map.
```JS
window.maps = {
// First Map
Bedroom: { // creating what the map will look like
    lowerSrc: "img/ (image link)",
    upperSrc: "img/ (image link)",
    gameObjects: { // adding game objects in the map
        npc1: new npc1({
            x: 10,
            y: 11,
        }),
        npc2: new npc2({
            x: 5,
            y: 6,
        })
    }
}
// Second Map
Kitchen: {
    lowerSrc: "img/ (image link)",
    upperSrc: "img/ (image link)",
    gameObjects: {
        npc3: new npc3({
            x: 14,
            y: 15,
        }),
        npc4: new npc4({
            x: 20,
            y: 21,
        })
        npc5: new npc5({
            x: 25,
            y: 26,
        })
    }
}
}
```
* When creating a map, you first need to create a variable. Inside the variable, you can add the background of what your map will look like and game objects. In the code above, I created two variable, kitchen and bedroom. Inside each variable, I added different game objects like npc1 and npc4. In addition, I also added what the background will look like for each map using `lowerSrc: "img/ (image link)", upperSrc: "img/ (image link)",`. I added a `lowerSrc` and `upperSrc` because the `lowerSrc` will help create the base of the map and `upperSrc` will help create the anything on top of the base.

* Something I am going to try next is grid based movement, where the user can move the sprite using the arrow keys.
#### Grid Based Movement
* Today I learned about how to move the sprite using the arrow keys.
```JS
class DirectionInput {
    this.heldDirections = [];

    this.map = {
        "ArrowUp": "up",
        "KeyW": "up",
        "ArrowDown": "down",
        "KeyS": "down",
        "ArrowLeft": "left",
        "KeyA": "left",
        "ArrowRight": "right",
        "KeyD": "right",
    }
}

init() {
    document.addEventListener("keydown", e => {
        console.log(e.code);
        const dir = this.map[e.code];
    });
}
```
* In the code above, I created different arrow keys to move in different direction when the arrow keys is clicked using `"ArrowUp": "up"`. In addition, after I created the different arrow keys, I run the code by using `document.addEventListener()`. `document.addEventListener()` helps the computer run the code inside the function when a certain key is pressed. Inside `document.addEventListener()`, I run the code using `const dir = this.map[e.code];`. `this.map[e.code];` helps find the function called this.map and grab the code that is the same as the arrow keys that you pressed.

* Something I am going to try next is character animations, where the sprite changes position when the sprite moves in a different direction.
#### Character Animations
* Today, I learned about how to make a sprite change into a different position when the sprite moves in a different direction using sprite sheets.
```JS
this.animations = config.animations || {
    "idle-down": [ [0,0]], // current position
    "walk-down": [ [1,0],[0,0],[3,0],[0,0] ], // when the sprite is not moving, it will create this animation.
}

// how long we want each game loop frame to be before it goes to the next frame
this.animationFrameLimit = config.animationFrameLimit || 16;
this.animationFrameProgress = this.animationFrameLimit;

get frame() {
    return this.animations[this.currentAnimation][this.currentAnimationFrame]; // helps run the code
}

this.currentAnimation = "walk-down";
```

```JS
const [frameX, frameY] = this.frame;

// helps draw the image of the sprite
// when the sprite changes positon, the current animation frame will change into the second animation frame.
this.isLoaded && ctx.drawImage(this.image,
 frameX * 32, frameY * 32,
 32, 32,
 x, y,
 32, 32,
)
```
* In the code above, you create the position of the sprite using `"walk-down": [ [1,0],[0,0],[3,0],[0,0] ],` `[0, 0]` helps tell us the animation frame we are using when the sprite is walking down. In addition, after we finsih creating the animation frame, we need to create a time for how long we want the animation loop to be before it goes to the next frame. After we finish creating the frame time, we draw the image by using `frameX * 32, frameY * 32,` , where frameX and frameY changes every time in the game loop.
* One challenge I faced was when I was learning about the updateAnimationProgress function. I was confused why when we reset the counter, we need to add 1 to `this.currentAnimationFrame`. In addition, I tried to comment out the code and noticed that if we didn't add 1 to the currentAnimationFrame, the current animation frame will always be the same.
```JS
updateAnimationProgress(){
    // Downtick frame progress
    if (this.animationFrameProgress > 0){
        this.animationFrameProgress -= 1;
        return;

    // Reset the counter
    this.animationFrameProgress = this.animationFrameLimit;
    this.currentAnimationFrame += 1;
    }

    if (this.frame === undefined){
        this.currentAnimationFrame = 0;
    }
}
```
#### Walls and Collisions
* Today, I learned about walls and collisions, where the sprite can not move through tables and game objects in the map.
```JS
walls: {
    [utils.asGridCooord(7,6)]: true,
    [utils.asGridCooord(8,6)]: true,
    [utils.asGridCooord(7,7)]: true,
    [utils.asGridCooord(8,7)]: true,
}

asGridCoord(x, y){
    return `${x*16}, ${y*16}`
}
```
* In the code above, we create a new variable inside the map called walls. Inside the variable, we set each position of the game object to true. To find the position of the game object, we can find the position of each game object through counting the positions of the boxes in the spritesheet. When the position of the object is true, the sprite can not walk through the game object.
<!--
* Links you used today (websites, videos, etc)
* Things you tried, progress you made, etc
* Challenges, a-ha moments, etc
* Questions you still have
* What you're going to try next
-->
