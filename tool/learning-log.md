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
* **IMPORTANT:** To prevent a infinite loop from happening, we put code we want to run **INSIDE** or **AFTER** **requestAnimationFrame()**

* These few weeks, I made a canvas for how big I wanted the game to be. In addition, after I finish making the canvas for my game, I started putting objects, sprites, and background on my canvas. Lastly, I started making loops to make the object appear forever as well as making the movements move constantly when you click on the mouse.
## **Winter Break (12/25/2023 - 1/1/2023)**
* Link: https://www.youtube.com/watch?v=fyi4vfbKEeo&list=PLcjhmZ8oLT0r9dSiIK6RB_PuBWlG1KSq_
#### Maps
* Today I learned about how to create the appearance of the map and how to add game objects inside the map.
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
* When creating a map, you first need to create a variable. Inside the variable, you can add the background of what your map will look like and game objects. In the code above, I created two variable, kitchen and bedroom. Inside each variable, I added different game objects like npc1 and npc4. In addition, I also added what the background will look like for each map using `lowerSrc: "img/ (image link)", upperSrc: "img/ (image link)",`. I added a `lowerSrc` and `upperSrc` because the `lowerSrc` will help create the base of the map and `upperSrc` will help create anything on top of the base.

* Something I am going to try next is grid based movement, where the user can move the sprite using the arrow keys.
#### Grid Based Movement
* Today I learned about how to move the sprite using the arrow keys.
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
* In the code above, you create the position of the sprite using `"walk-down": [ [1,0],[0,0],[3,0],[0,0] ],` `[0, 0]` helps tell us the animation frame we are using when the sprite is walking down. In addition, after we finish creating the animation frame, we need to create a time for how long we want the animation loop to be before it goes to the next frame. After we finish creating the frame time, we draw the image by using `frameX * 32, frameY * 32,` , where frameX and frameY changes every time in the game loop.
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
## **1/8/2024 - 1/29/2024**
#### Typewriters & Scene Transitions
* Link: Link: https://www.youtube.com/watch?v=fyi4vfbKEeo&list=PLcjhmZ8oLT0r9dSiIK6RB_PuBWlG1KSq_
* Today I learned about creating a text message inside a cut scene.
##### How to create a text message inside a cut scene
```JS
this.map.startCutscene([
    {type: "textMessage", text: "This is the very first message!"}
])
```
In the code above, when you want to create a text message inside the scene, you first need to start the cut scene by using `this.map.startCutscene([])`. Inside the cut scene, you can add text messages using `{type: "textMessage", text: "This is the very first message!"}`.

#### How to make the text appear one by one
* Link:https://www.youtube.com/watch?v=fyi4vfbKEeo&list=PLcjhmZ8oLT0r9dSiIK6RB_PuBWlG1KSq_
* Today, I learned about how to make the text appear one by one as well as creating the speed of when each word appear.
```JS
// css
.TextMessage span{
    opacity: 0;
}
.TextMessage span.revealed{
    opacity: 1;
}
```
* In the code above, when the text message is not revealed, it will not appear on the screen. In addition, when the text message is revealed, it will appear on the screen.
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
* In the code above, inside the for each loop, when you run the code, each letter will appear one by one. In addition, if we want one word to appear one by one, we can create a new for loop, where we do not use `this.text.split("")`.

* One challenge I had was when I was trying out how to use `delayAfter: character === " " ? 0: this.speed`. I was confused what `?` mean in the code. After trying out the code, I learned that `?` mean passing a number into the empty string.
## (1/22/2024 - 1/30/2024)
Link: https://www.youtube.com/watch?v=fyi4vfbKEeo&list=PLcjhmZ8oLT0r9dSiIK6RB_PuBWlG1KSq_
* This week, I learned about building a table, where when the user touches the table, the user can craft different things. In addition, this week, I also learned about how to create a text message when the user touches the table.
#### Step 1
* I first started by making the table appear on the screen. I started by adding a table into the map first by creating a new game object inside my map called `Main Map`. Then, when I was watching the tutorial, I learned about `storyFlag`, where the storyFlag can help tell us if the food on the table is crafted yet.
```JS
window.MainMaps = {
    table: new table({ // creating a new game object
        // position of the table
        x: 8,
        y: 15,
        storyFlag: "TABLE" // helps tell us if the user crafted a food or not
    })
}
```
#### Step 2
In addition, after I added the `storyFlag` inside my new game object. I created a new class to make my table responsive after the user touches the table. In the beginning, I tried by making the table appear a text message everytime the user touches the table. I created a event inside `this.talking`, so that whenever the sprite touches the table, it will appear a text message saying `This is a table.`
```JS
class CraftTable extends GameObject {
    this.storyFlag = config.storyFlag;
    this.talking = [{
        events: [ // the event will run everytime the user touches the table
            {type: "textMessage", text: "This is a table"},
        ]
    }]
}
```
* Next week, I am going to try making different text messages when the user wants to craft a new food or if the food has already been crafted.
## (2/26/2024 - 3/4/2024)
Link: https://www.youtube.com/watch?v=fyi4vfbKEeo&list=PLcjhmZ8oLT0r9dSiIK6RB_PuBWlG1KSq_
* This week, I continued learning about builidng a table, where when the user touches the table, the user can craft different things. Last few weeks, I learned about adding a table inside a map as well as making a text message appear when the user touches the table. This week, I am going create different text messages that tells the user if they are creating a new food or if the food has already been crafted.

#### Step 3
I started by adding `food` inside the table, where it grabs the ID of the food (hamburger and french fries), where when the storyFlag is true, the food will appear.
```JS
window.OverworldMaps = {
    table: new table({ // creating a new game object
        // position of the table
        x: utils.withGrid(3),
        y: utils.withGrid(7),
        storyFlag: "TABLE" //
        foods: ["a035", "c358"], // a035 and c358 are the id for my hamburger sprite and french fries sprite
    })
}
```
#### Step 4
Inside the class `CraftTable`, I added a `required: [this.storyFlag],`, where only when there is a `storyFlag` inside the game object, it will appear a text message. In addition, I also added a new event when the the user is crafting a new food. In the beginning, I added a new text message saying that `you are crafting a new food..`, when the text message disappears, it will ask the user to pick a food. The food id will be stored into `foods`, so that when the update function runs, the food will appear on the table.
```JS
class CraftTable extends GameObject {
    this.storyFlag = config.storyFlag;
    this.food = config.food; // pass in the id of the food when the user clicks on a food that they want to craft
    this.talking = [{
        required: [this.storyFlag], // if the game object has a storyFlag, the event will run
        events: [
            {type: "textMessage", text: "You have already crafted this food"}, // the text message will appear when the required is true
        ]
    }]
},
{
    events: [ // when the user is crafting a nnew food
        {type: "textMessage", text: "You are crafting a new food..."}, // creating a new message
        {type: "craftingMenu", foods: this.food}, // when the user chooses a food, the id of the food will be stored inside this.food
        {type: "addStoryFlag", flag: this.storyFlag}, // grabs the storyFlag from map and storing the storyFlag in flag
    ]
}
```

#### Step 5
Then, I learned about creating a update, where the game object on the table can disappear when the food is crafted. In the beginning, I was very confused what does the `? "used-down"` and `:"unused-down";` do when the update function runs. When I tried changing the text message inside the quotation marks, there was an error. However, through debugging and watching the tutorials again, I learned that when the update function runs, it first check if the current animation is equal to `"used-down"`, if it is not equal to `"used-down"`, it will change the current animation to `"unused-down"`, making the food on the table disappear.
```JS
update(){
    this.sprite.currentAnimation = playerState.storyFlag[this.storyFlag]
    ? "used-down"
    : "unused-down";
}
```
## 3/4/2024 - 3/10/2024
* This week, I started working on my MVP for my game. I made a canvas for my game as well as making my sprites move.
In the beginning, I first created the canvas for my game using ` <img  class = "game-canvas blue "src = "link to the image">`.
```JS
<div class = "game-container">
       <img  class = "game-canvas blue "src = "img/sep-room.png">
</div>
```
* When I inspect it, I realized that the image was too large, so I changed the size of the canvas as well as created a border for my canvas.
```JS
 * {
    box-sizing: border-box;
}

  .blue{
     width: 1000px;
     height: 600px;
    }
```
* After I finish creating the canvas, I started adding all the sprites inside my game as well as making the sprite move using the up, down, left, and right keys. In the beginning, I first added all my sprites inside the game using `<img  class = "game-canvas size "src = "img/sprite-1.png">` in html.
```html
 <img  id="num1" class = "game-canvas size position1" src = "img/sprite-1.png">
 <img  id="num1" class = "game-canvas size position2" src = "img/sprite-2.png">
 <img  id="num1" class = "game-canvas size position3" src = "img/sprite-3.png">
 <img  id="num1" class = "game-canvas size position4" src = "img/sprite-4.png">
 <img  id="num1" class = "game-canvas size position5" src = "img/sprite-5.png">
```
Then, I grab the id of each sprite and make all the sprite be able to move using `document.addEventListener("keydown", e => {});`
```JS
document.getElementById("num1").addEventListener("keydown", e => {
        "ArrowUp": "up",
        "ArrowDown": "down",
        "ArrowLeft": "left",
        "ArrowRight": "right",
    });
```
However, when I inspect it using `http-server`, it wasn't working. The sprite was not moving when I click on the up, down, left, and right button. Then, I look through my notes again and found out that you use `"ArrowUp": "up",`, it is only declaring `ArrowUp` to `up` but it is not calling `"ArrowUp": "up",`.
## 3/11/2024 - 3/18/2024
* Link:https://www.w3schools.com/
* Link:https://www.youtube.com/watch?v=fyi4vfbKEeo&list=PLcjhmZ8oLT0r9dSiIK6RB_PuBWlG1KSq_
* This week, I continued working on my MVP for my game. I made a clickable map using `.addEventListener("click", myFunction);`. In the beginning, I added all the map and made all the map the same size and position. In addition, I also added a id for each map.
```html
 <div class = "game-container">
       <img class = "game-canvas blue" id ="map1" src = "img/sep-room.png">
       <img class = "game-canvas purple" id ="map2" src = "img/kitchen.png">
       <img class = "game-canvas green" id ="map3" src = "img/testRoom.png">
    </div>
```
* After I finish adding all my map, I grab the id for each map and made the map clickable using `.addEventListener("click", myFunction);`.
```JS
    document.getElementById("map1").addEventListener("click", myFunction);
    document.getElementById("map2").addEventListener("click", myFunction2);
    document.getElementById("map3").addEventListener("click", myFunction3);
```
* Then, inside each function, I made the next map appear when the user clicks on the map, while the other maps disappear. In addition, I used `document.getElementById("map2").style.visibility= "hidden";` to make the map disappear and `document.getElementById("map2").style.visibility= "visible";` to make the appear.
```JS
 function myFunction(){
    document.getElementById("map1").style.visibility= "hidden";
    document.getElementById("map2").style.visibility= "visible";
    document.getElementById("map3").style.visibility= "hidden";
        }

 function myFunction2(){
    document.getElementById("map1").style.visibility= "hidden";
    document.getElementById("map2").style.visibility= "hidden";
    document.getElementById("map3").style.visibility= "visible";
        }

 function myFunction3(){
    document.getElementById("map1").style.visibility= "visible";
    document.getElementById("map2").style.visibility= "hidden";
    document.getElementById("map3").style.visibility= "hidden";
        }
```
* Next week, I am going to continue building my MVP. In addition, I am going to add all the game objects inside my game and make a score board.
## 3/19/2024 - 3/25/2024
* Link:https://www.w3schools.com/
* Link:https://www.youtube.com/watch?v=fyi4vfbKEeo&list=PLcjhmZ8oLT0r9dSiIK6RB_PuBWlG1KSq_
* This week, I continued building my MVP for my game. Last week, I created a clickable map and made the sprites movee in the game. Today, I am going to create a score board, where when the player finds an object in the map, the score will increase by 1.

* In the beginning, I first started by adding all the game objects into the game. In addition, I made all the game objects disappear when it is clicked using `document.getElementById("table").style.visibility= "hidden"`.
```Java

document.getElementById("table").addEventListener("click", myFunction5);
document.getElementById("pizza").addEventListener("click", myFunction5);
document.getElementById("cupcake").addEventListener("click", myFunction5);
document.getElementById("rice").addEventListener("click", myFunction5);
document.getElementById("cookie").addEventListener("click", myFunction5);
document.getElementById("popcorn").addEventListener("click", myFunction5);
document.getElementById("bread").addEventListener("click", myFunction5);


function myFunction5(){
    document.getElementById("table").style.visibility= "hidden";
    document.getElementById("cupcake").style.visibility= "hidden";
    document.getElementById("pizza").style.visibility= "hidden";
    document.getElementById("rice").style.visibility= "hidden";
    document.getElementById("cookie").style.visibility= "hidden";
    document.getElementById("popcorn").style.visibility= "hidden";
    document.getElementById("bread").style.visibility= "hidden";
}
```
* In the code above, when `table, cupcake, pizza, rice, cookie, popcorn, and bread` is clicked, `myFunction5` will run and the game object will disappear. After I finish making all the game objects be able to disappear, I started making the score board for my game. In the beginning, I first started by adding a text message using `text();`
```Java
var num = 0;
text("Score :" + " " + num, 0, 50);
// In the code above, I created a variable called num to help keep track of the the score. In addition, then I created a text called score and the position of the text is at (0, 50)
```
* After I finish adding the text message inside the game, I started making the score increase whenever a game object is clicked. As a result, I first try putting it inside `myFunction5`. I was scared that it will only increase the score by 1 one time.
```Java
function myFunction5(){
    document.getElementById("table").style.visibility= "hidden";
    document.getElementById("cupcake").style.visibility= "hidden";
    document.getElementById("pizza").style.visibility= "hidden";
    document.getElementById("rice").style.visibility= "hidden";
    document.getElementById("cookie").style.visibility= "hidden";
    document.getElementById("popcorn").style.visibility= "hidden";
    document.getElementById("bread").style.visibility= "hidden";
    num++;
}
```
However, when I run it in `http-server`, it worked!

* Next week, I am going to make sprites be able to go inside houses and building inside the game.
<!--
* Links you used today (websites, videos, etc)
* Things you tried, progress you made, etc
* Challenges, a-ha moments, etc
* Questions you still have
* What you're going to try next
-->
