##### Maya Goldstein
##### July 2017

# Mr. Fun Guy's Wild Ride

---

### Specs

* Technologies Used: HTML, CSS, JavaScript, jQuery, Velocity.js
* Music:
  * "Cuckoo" - Tipper
  * "Raindrops on Roses" - An-ten-nae feat. Alice D
* Background graphics: giphy

---

LINK TO LIVE SITE:

https://mayagold.github.io/Cosmonaut

---

### Premise

Help a computer character, "Mr. Fun Guy,"  take a trip through outer space on his spaceship fueled by magic mushrooms. Click on the mushrooms to try to earn fuel points. Each round, they get more difficult to click on. When you make it through all seven rounds, you win the game and Mr. Fun Guy's spaceship takes off.

---

### This was my first-ever attempt to build a game using JavaScript.

I wanted to play with CSS animations and jQuery animations. My original idea was to make a game in which animated objects move across the page and you have to click on them to earn points. Naturally, I chose mushrooms to be the animated objects.

---

### Breakdown

![Modal: Start Game](/screen_captures/pageload.png?raw=true)

The page loads and displays a start modal. This modal contains the directions for the game, instructing the player to click on the mushrooms that appear on screen, and a start button.

An event listener attached to the start button triggers audio.
  * The first song begins playing when you click the start button. ("Cuckoo" by Tipper)
  * An event listener attached to the first song starts the second song when the first song finishes playing. ("Raindrops on Roses feat. Alice D" by An-ten-nae)

Clicking on the start button also hides the start modal, and displays the game space. A timer immediately begins counting down from 30 seconds and 10*(roundNumber) mushrooms appear on screen (10 mushrooms for round 1, 20 for round 2, etc.). They have different animations for each round.

The mushrooms are randomly assigned a class of "normal", "poisonous," or "magic" using Math.random().

The mushrooms are randomly assigned a top and left margin using Math.random() - this gives the illusion that they are "scattered" across the screen randomly.

The mushrooms are given different animations for each round, using velocity.js.

An event listener is attached to each mushroom. Clicking on any mushroom will adjust the player's score.

Clicking on a magic mushroom will increase your points by 1. The magic mushroom will spin and change color, rotating through the rainbow, and then become opaque (using css animation).

Clicking on a poisonous one will decrease your points by 1. The poisonous mushroom will vibrate and become opaque (using css animation).

Clicking on a normal one will not change the score. It will remove the normal mushroom from the page.

Each mushroom can only be clicked on once. Then the event listener for that mushroom is turned off.

---

### Rounds

At the end of each round, a modal will pop up.

![Modal: Next Round](/screen_captures/next_round_modal.png?raw=true)

If you have enough points to move on to the next round, a message will appear that will tell you you can move on, and you do so by clicking a button with an event listener attached, which triggers the next round.

The body background is reassigned for each new round to display a different gif.

![Modal: Repeat Round](/screen_captures/repeat_modal.png?raw=true)

If you don't have enough points, the modal will prompt you to repeat the round.

---

### Win State

![Modal: You Win](/screen_captures/win_modal.png?raw=true)

You win the game when all seven rounds have been completed and all colors are on the page.

Button gives you the choice to play again.

---

### Lose State

![Modal: You Lose](/screen_captures/lose_modal.png?raw=true)

You lose the game if your score falls below zero

You destroyed the spaceship's engine by trying to fuel it with poisonous mushrooms. Game over.

Button gives you the choice to play again.

---
# Functionality

### Event Handlers

**startGame();** - attached to start button - starts audio, sets up first round with score=5 and time=30, hides modals, displays the div containing the mushrooms

**clickShrooms();** - attached to mushroom images - triggers different CSS animations for poisonous, magic and normal mushrooms

**nextRound();** - attached to next-round-button - triggers setUpRound and hides the modal that contains it

**repeatRound();** - attached to repeat-round-button - triggers setUpRound and hides the modal that contains it

**restartGame();** - attached to start button - contained in modal that pops up when you lose the game - starts game over

**newGame();** - attached to start button - contained in modal that pops up when you win the game - starts game over

---

### Game Round Object

Contains a property roundNumber that updates based on round number.

**clearBoard();** method removes all mushrooms from their container div

**generateShrooms(num);** method creates num shrooms and assigns them a random class and location on the page

**setTimer();** sets the timer to count down from 30 seconds and calls **checkForWin();** when time===0

**roundRepeat();** calls the repeat round modal

**roundNext();** calls the next round modal

**roundAnimation(round);** assigns a different animation and body background based on the round number

---

**setUpRound();** calls the following functions:

* round.clearBoard();
* round.generateShrooms(round.roundNumber*10);
* round.setTimer();
* round.roundAnimation(round.roundNumber);
* eventHandlers.clickShrooms();

**checkForWin();** compares the score and the round number and determines whether the game will move on to the next round, or repeat the same round, or whether the user has won or lost the game

---

### Approach

1. Coded HTML
2. Coded Functionality - made the game playable without any cool animation using JavaScript and jQuery. Make the modals work using CSS and event handlers
3. Coded basic CSS. Added event listeners to mushrooms and CSS animations when you click them
4. Updated the HTML and game premise as I went along and my idea developed
5. Added features: Audio, velocity animations, and background gifs

---

### ONGOING GOALS

* Media queries to improve cell phone usability
* Improve CSS
* Add audio playlist in HTML
