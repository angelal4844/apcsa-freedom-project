# Entry 3
##### 2/12/2024

### Context
These few weeks, I continued tinkering with my tool, Javascript. I learned to create maps, text message, grid based movement, and many more. During my journey in learning my tool, I faced many challenges as well as aha moments.
### What I learned
* Link:  https://www.youtube.com/watch?v=fyi4vfbKEeo&list=PLcjhmZ8oLT0r9dSiIK6RB_PuBWlG1KSq_
#### Maps
* When creating a map for the game, you first need to create a variable. Inside the variable, you can add game objects, background, and the position of the game object.
```JS
window.maps = {
// First Map
Bedroom: { // creating what the map will look like
    lowerSrc: "img/ (image link)", // what the base of the map will look like
    upperSrc: "img/ (image link)", // what the top of the map will look like
    gameObjects: { // adding game objects in the map
        npc1: new npc1({
            // position of npc1
            x: 10,
            y: 11,
        }),
        npc2: new npc2({
            // position of npc2
            x: 5,
            y: 6,
        })
    }
}
// Second Map
Kitchen: {
    lowerSrc: "img/ (image link)", // what the base of the map will look like
    upperSrc: "img/ (image link)", // what the top of the map will look like
    gameObjects: {
        npc3: new npc3({
            // position of npc3
            x: 14,
            y: 15,
        }),
        npc4: new npc4({
            // position of npc4
            x: 20,
            y: 21,
        })
        npc5: new npc5({
            // position of npc5
            x: 25,
            y: 26,
        })
    }
}
}
```
* In the code above, I created two variables, a kitchen and a bedroom. Inside each variable, I added the background of what each map is going to look like and added sprites inside the map. In addition, when I added the sprites in each map, we also need to write the position of where we want the sprite to be. Moreover, I also added what the background will look like for each map using `lowerSrc: "img/ (image link)", upperSrc: "img/ (image link)",`. I added a `lowerSrc` and `upperSrc` because the `lowerSrc` will help create the base of the map and `upperSrc` will help create anything on top of the base.
#### Grid Based Movement
`document.addEventListener("keydown", e => {});` --> Helps call the arrow key that was declared
`"ArrowUp": "up"` --> helps declare the arrow key
```JS
class DirectionInput {
    this.heldDirections = [];

    this.map = {
        "ArrowUp": "up", // when the user presses the up arrow key, the sprite will move up
        "KeyW": "up", // when the user presses the letter W on the keyboard, the sprite will move up
        "ArrowDown": "down", // when the user presses the down arrow key, the sprite will move down
        "KeyS": "down", // when the user presses the letter S on the keyboard, the sprite will move down
        "ArrowLeft": "left", // when the user presses the left arrow key, the sprite will move left
        "KeyA": "left", // when the user presses the letter A on the keyboard, the sprite will move left
        "ArrowRight": "right", // when the user presses the right arrow key, the sprite will move right
        "KeyD": "right", // when the user presses the letter D on the keyboard, the sprite will move right
    }
}

init() {
    document.addEventListener("keydown", e => {
        console.log(e.code);
        const dir = this.map[e.code];
    });
}
```
* In the code above, I created different arrow keys to move in different direction when the arrow keys is clicked using `"ArrowUp": "up"`. In addition, after I created the different arrow keys, I run the code by using `document.addEventListener()`.`document.addventListener()` helps the computer run the code inside the function when a certain key is pressed. Inside `document.addeventListener()`, I run the code using `cost dir = this.map[e.code];`.`this.map[e.code];` helps find the function called `this.map` and grab the code is the same as the arrow keys that you pressed.
#### Character Animations
* `Character Animations` --> Helps change the animation frame when the sprite is going in different direction.
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
* In the code above, you create the position of the sprite using `"walk-down": [ [1,0],[0,0],[3,0],[0,0] ],` `[0, 0]`.`[0, 0]` helps tell us the animation frame we are using when the sprite is walking in different direction. In addition, after we finish creating the animation frame, we also need to create a for how long we want the animation loop to be before it goes to the next frame. In the code above, the time is equal to the animation frame or 16. After we finish creating the frame time, we draw the image by using `frameX * 32, frameY * 32`, where frameX and frameY changes every time in the game loop. In addition, 32 is the length and width of each animation frame.
#### Walls and Collisions
`[utils.asGridCooord(7,6)]: true,` --> when the position of the game object is set to true, the sprite can not move through the game objects in the map.
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
* In the code above, we create a new variable inside the map called walls. Inside the variable, we set each position of the game object to true. To find the position of the game objeect, we can find the position of each game object through counting thee positions of the boxes in the spritesheet. When the position of the object is true, the sprite can not walk through the game object.

* **REMEMBER:** We need to set **each side** of the game object to true. For example, if the game object is a table, we need to set all 4 sides of the table to true

#### Text message
* `{type: "textMessage", text: "This is the very first message!"}` --> Helps create a text message
```JS
// css
.TextMessage span{
    opacity: 0;
}
.TextMessage span.revealed{
    opacity: 1;
}
```
* In the code above, we first create a text message. In addition, if we want the text message to appear one by one, we first set the opacity of all the text message to 0. Then, when the text message is revealed, we set the opacity of the text message to 1.
```JS
// how to change the text and speed
class RevealingText {
    constructor(config) {
        this.element = config.element;
        this.text = config.text;
        this.speed = config.element || 70; // speed of the text message

        this.timeout = null;
        this.isDone = false;
    }

    init(){
        let character = []; // empty array
        this.text.split("").forEach(character => { // spliting each string in the array
        // {Hi} --> {"H", "i"}

            let span = document.createElement("span"); // creating each span for the array
            span.textContent = character;  // adding words into the empty array
            this.element.appendChild(span); // adding the span into each string

            character.push({
                span,
                delayAfter: character === " " ? 0: this.speed // the speed and time before the second text message appears
            })
        })
    }
}
```
* When we finish setting the opacity of the text message, we also need to add a time of when we want each word to appear on the screen. In the code above, we first make the word appear one by on using `this.text.split("")`. Then, we add all the words inside a empty array and add span to each string. After we made the words appear one by one, we created the speed and time for each word.
### Aha Moments and Challenge
* One challenge I faced was when I was learning about character animation. I was confused when we reset the counter, why do we need to add 1 to `this.currentAnimationFrame`. In addition, I tried to comment out the code and noticed that if we didn't add 1 to the `currentAnimationFrame`, the current animation frame will always stay the same.
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
* Some aha moments I found was when I was learning about time and speed. I learned that `?` means passing a number into a empty string.
```JS
delayAfter: character === " " ? 0: this.speed
```
* In addition, I also learned that you can add span to each string using `this.element.appendChild(span);`.

### Planning
* After I finished learning my tool, I started to plan what I want the background and game object to be. In addition, during these few weeks, I drew out what I want my background of the game to be.

### Skills
* Some skills I learned when tinkering my tool and planning out the background and sprites for my game is time management, creativity, and how to google. These few weeks, I drew out different ideas for my game and what I want to include in my game. In addition, I learned to organize my time by watching tutorials and taking notes every morning during my winter break. Moreover, I also learned how to google by finding different tutorials to watch if I am confused.
### EDP
* Last blog, I am on stage 2, research the problem. This blog, I am currently on stage 2, research the problem and stage 3, brainstorm possible solutions. These few weeks, I continued on learning and tinkering with my tool. I learned to create maps, how to make sprite move, text messages and many more. In addition, these few weeks, I started planning out what I want my game to be, backgrounds, and sprites. Next blog, I would start building my MVP and beyond MVP.
### Spring Break
* During spring break, I would finish my planning and decide what my MVP and beyond MVP is. In addition, I want to finish drawing all my backgrounds and sprites.

[Previous](entry02.md) | [Next](entry04.md)

[Home](../README.md)