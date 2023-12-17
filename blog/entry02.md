# Entry 2
##### 12/18/2023

### Context
These few days, I started tinkering with my tool, Javascript. In addition, I learned to create the canvas for the game, import images, as well as loops. During my journey in tinkering my tool, I faced many challenges as well as aha moments when learning the tool.

### Tool (10/27/23 - 12/4/2023)
#### How to place images on a canvas
* **IMPORTANT**: **ORDER MATTERS WHEN PLACING IMAGES**
* PUT IMAGES YOU WANT AS BACKGROUND **FIRST**, THEN THE OTHER SPRITES

* In the code below, `this.animations` helps grab the class called `animation` and set the position to `0`. When we set the position to `0`, we also need to set the `currentAnimationFrame` to `0`. After, everything is set to `0`, we can change the position of the sprite using `this.gameObject.x * 16 - 8` and draw out the sprite using `ctx.drawImage(this.image, 0, 0, 32, 32, x, y, 32, 32)`.
```Javascript
// Configure Animation and Initial State
this.animations = config.animations || {
    idleDown: [
        [0,0] // set the position to 0
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
#### Game Objects
* `Game Object` --> Game objects are different sprites in the game.
* `const cupcake = new GameObject({})` --> helps create a new GameObject. Inside the new GameObject, you can create the position of where you want the sprite to be
```JS
const cupcake = new GameObject({
    x: 7,
    y: 10,
})
const menu = new GameObject({
    x: 7,
    y: 9,
})
```
In the code above, I wanted to create a menu and a cupcake for my bakery. In addition, I used `const cupcake = new GameObject({})` to create a new sprite and set the initial position of the sprite to 7, 10.

* After I set the initial position of the sprite to 7, 10, I wanted the sprite to move at different position too.
```JS
draw(ctx) {
const x = this.game0bject.x * 16 - 8;
const y = this.game0bject.y * 16 - 18;
}
```
In the code above, I learned that when you want to change the position again, you need to use `this.game0bject.x * 16 - 8`. I noticed that it is very similar to `Math.random()`, the `*11` tells us that it is going to choose a random number from 0 to 10. In addition, the `-5` tells us that it is going to shift to the left 5 times, so it is going to choose a random number from -5, 5.
* In `Math.random()`,
```Java
Math.random(); // [0,1) start
Math.random()*11 // [0,11) scale
(int) (Math.random()*11) // [0,10] cast
(int) (Math.random()*11) - 5; // [-5,5] shift
```
* When we change the position of the sprite, it is the same as `Math.random()`, where the `*16` tells us where the position is, and the `-8` tells us if it is going to shift to the left or right.
```JS
draw(ctx) { // Helps draw the sprite
const x = this.game0bject.x * 16 - 8;
// In this code above, the position of x is going to be [-8, 8]. The * 16, tells us that the position of the sprite is [0, 16]. The -8 tells us that it is going to shift to the left 8 times, so it is going to be [-8, 8].
}
```
#### Loops
* `Loops` --> Helps load all the sprites in the game and helps repeat the movement we want the sprite to do using `requestAnimationFrame() => {}`.
```JS
startGameLoop() {
    const step = () => {
        requestAnimationFrame() => {
            step();
        })
      }
      step();
    }
```
* In the code above, we first start the loop by using `startGameLoop() {}`. In addition, we create the movement of what we want the sprite to do using `const step = () => {};` Inside `const step = () => {};`, we use ` requestAnimationFrame() => { step(); })`, where everytime the sprite step, it will create a animation frame every time the sprite `step`.

### Aha Moments and Challenges
* One challenge I faced was finding where each variable is. For example, in the code below, I was really confused with `this()` because I wasn't really sure which method `this()` is referring to. In addition, I tried rewatching the tutorial and found out that `this()` is referring to the class called image.
```JS
ctx.drawImage(this.image,
0, 0,
32, 32,
x, y,
32, 32,
)
```
* Some aha moments I found was when I was learning about loops. I learned that everytime you want to create a movement, you need to put it inside `requestAnimationFrame() => {}` or create a new `requestAnimationFrame() => {}`. If you put it outside of `requestAnimationFrame() => {}`, it will cause a infinite loop.
* **IMPORTANT:** To prevent a infinite loop from happening, we put code we want to run **INSIDE** or **AFTER** **requestAnimationFrame()**
### Skills
Some skills I learned is time management, how to learn, and how to google. These few weeks, I learned to organize my time by watching tutorials every Monday and taking notes on what I made and challenges/aha moments I noticed during my journey in tinkering my tool. In addition, I learned how to google by watching different tutorials and rewatching the tutorials when I don't understand how the code works. In conclusion, I also learned how to learn by watching different videos and tutorials on Youtube on how to create different games using Javascript.

### EDP
Last blog, I am on stage 1, define the problem and stage 2, research the problem. This blog I am currently on stage 2, research the problem. These few weeks, I continued on tinkering with my tool. I learned about how to use loops to create different movements to the sprite as well as changing the position of the sprite and how to load the sprite. Next blog, I would continue tinkering with my tool and start planning out what my project will look like.
### Winter Break
During winter break, I would finish learning all the topics in Javascript and make a mini project using everything I learned while tinkering my tool to make sure that I understand how to use the code.

[Previous](entry01.md) | [Next](entry03.md)

[Home](../README.md)