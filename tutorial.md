# Retro Game Lab Camp: Retro Pong!

## Introduction
Welcome to **Retro Pong!** 🕹️  
In this game, we'll re-create the retro classic Pong — but with a modern twist!  
You'll learn how to make:

- your **own Sprite kinds** 
- use **functions** to keep code neat 
- detect **sprite overlaps** 
- track **scores for two players**.






## Creating a Background!

Let's start with the most basic part of *every* project, the background!

### Setting the Background

- :tree: From ``||scene:Scene||``, drag out ``||scene:set background image to []||`` and snap it inside your ``||loops:on start||`` container.  
- :mouse pointer: Click the [] to open the Image Editor and draw a cool background (or paste one like a blue court!).  

- :lightbulb: Sensei Tip — You can press **Gallery** and pick any preset to make your background colorful fast!








## Making Sprite Kinds

Normally, MakeCode Arcade has sprite kinds like **Player**, **Enemy**, and **Projectile**.  

But in Pong, we need our own kinds: **Blue**, **Red**, **Ball**, and the **Goals**!

### Let's make the custom Sprite Kinds!

- :paper plane: Find the ``||sprites: set mySprite to img [] of Kind [Player]||`` inside of the ``||sprites: Sprites||`` menu and place it onto your ``||loops: on start||`` container.

- :mouse pointer: Where it says ``||sprites: Kind [Player]||``, select the **drop down menu** and press **Add a new Kind...**

- :keyboard: Create 3 new Sprite Kinds: **Ball**, **RedGoal**, **BlueGoal** 

These create *new categories* for our sprites so we can detect which one overlaps which.  

You'll use these kinds in dropdowns inside the ``||sprites:on overlap||`` blocks later.








## Step 1: Player Paddle (Blue)
- :paper plane: From ``||sprites:Sprites||``, grab ``||sprites:set mySprite to []||``.  

- :mouse pointer: Draw a **blue vertical paddle** (about 8×32 pixels).    

- :tree: Add ``||sprites:set bluePaddle position to x(8) y(60)||`` under it.  

### Make It Move
- :game controller: Add ``||controller:move bluePaddle with buttons||``.  
- :mouse pointer: Change movement speed to vx = 0, vy = 50.  

Since vx = 0, the paddle only moves **up and down**, perfect for Pong!








## Step 2: Enemy Paddle (Red)
Now for the **AI paddle** on the right side!  
- :paper plane: Create another ``||sprites:set mySprite to []||``, draw a **red vertical paddle**, rename to ``||variables:redPaddle||``, and set kind to ||sprites:Red||.  

- :tree: Add ||sprites:set redPaddle position to x(152) y(60)||.  

Then add:

set redPaddle velocity to **(0, 50)**  

set redPaddle bounce on wall to **(true)**  

Now it moves up and down automatically and bounces off the screen edges — no controller needed!



## Step 3: The Goals
The goals are invisible "walls" that detect when the ball passes a side.  

### Red Goal (Left Side)
- :paper plane: Create a sprite (tiny vertical rectangle) for the red goal.  

Rename it to ``||variables:redGoal||`` and set its kind to ``||sprites:redGoal||``.  

- :tree: Set position x = 0.  

### Blue Goal (Right Side)
:paper plane: Create another sprite for the blue goal.  
Rename it to ``||variables:blueGoal||`` and set its kind to ``||sprites:blueGoal||`` .  
:tree: Set position x = 160.  

These detect when each player scores!

 

## Step 4: The Ball Function ⚽
We'll use a **function** to create and launch the ball.  
:functions: Go to ``||functions:Functions||`` → **Make a Function** → name it **createBall**.  

Inside the function, add:  
- :paper plane:``||sprites:set ballSprite to []||`` and draw a small **white circle** (about 8×8).  
- :paper plane: its kind to ``||sprites:Ball||``.  
- :paper plane:``||sprites:set ballSprite velocity to vx(50) vy(50)||``.  
- :paper plane: ``||sprites:set ballSprite bounce on wall to (true)||``.  

Now your function knows how to make and launch a new ball!

 

## Step 5: Start the Game
Inside your ``||loops:on start||`` container:  

- :info: Add:

``||info:info.player1.setScore(0)||``

``||info:info.player2.setScore(0)||``

- :computer: Then call your new function:

- :computer: ``||createBall()||``

Now both scores start at zero and a new ball appears.

 

## Step 6: Overlaps — The Magic of Collision 🎯
We'll use overlaps to bounce the ball and score points.

### Blue Paddle Overlap

:paper plane: Add ``||sprites:on overlap||`` with **Blue** and **Ball**.  

Inside it:

``||logic:otherSprite.vx = otherSprite.vx * -1||``
``||loops:pause(500)||``  

This bounces the ball and slows it briefly.

### Red Paddle Overlap

- :paper plane: Add another overlap: **Red** and **Ball**.  

Inside:

``||logic:otherSprite.vx = otherSprite.vx * -1||``
``||loops:pause(500)||``  



### Red Goal Overlap (Left Side)

- :paper plane: Add overlap **redGoal** and **Ball**.  

Inside:

``||info:info.player2.changeScoreBy(1)||``  
``||logic:otherSprite.vx = otherSprite.vx * -1||``  
``||loops:pause(500)||``

Now **Player 2 (Red)** scores a point when the ball hits the left wall.

### Blue Goal Overlap (Right Side)

- :paper plane: Add overlap **blueGoal** and **Ball**.  

Inside:

``||info:info.player1.changeScoreBy(1)||``  
``||logic:otherSprite.vx = otherSprite.vx * -1||``
``||loops:pause(500)||``

Now **Player 1 (Blue)** scores when the ball hits the right wall.

 

## Step 7: Test and Tweak
Press **Play ▶** and check:  
✅ Do both paddles move correctly?  
✅ Does the ball bounce off walls and paddles?  
✅ Do scores increase on each goal hit?

If your ball gets stuck, make sure you called createBall() inside on start.


## Step 8: Add Personality ✨

Try these challenge ideas!  
🎵 Play a sound each time the ball bounces: ``||music:play sound (ba-ding)||``  
🔥 Make the ball faster after every bounce!  
🎨 Redraw paddles with pixel art flair!  
🧠 Add a "win" screen when a player reaches 5 points.

## 🎉 You Did It!
You just built **Retro Pong!**  
You learned:
- How to create **custom sprite kinds**
- How to use **functions** to respawn objects
- How to use **sprite overlaps** for scoring and collision
- How to track **two players' scores**

Now challenge yourself — can you make it **two-player** using another controller? 😎
