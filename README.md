# Guessing Game

This is a simple guessing game implemented using JavaScript.

## Description

The "Guessing Game" is a JavaScript-based web application that allows users to play a guessing game. The program generates a random number between 0 and 10, and the player's objective is to guess that number correctly.

The game consists of two screens represented by HTML elements with the classes `screen1` and `screen2`. The first screen (`screen1`) displays the game instructions and provides an input field where the player can enter their guess. The second screen (`screen2`) is initially hidden and appears when the player guesses the correct number or chooses to play again.

## Installation

To use the Guessing Game, follow these steps:

1. Create an HTML file and include the following HTML code:

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Guessing Game</title>
  <link rel="stylesheet" href="./style.css">
</head>

<body>
  <main>
    <div class="screen1">
      <h1>Guessing Game</h1>
      <p>Guess a number between 0 and 10</p>
      <form>
        <input id="inputNumber" type="number">
        <button id="btnTry">Guess</button>
      </form>
    </div>

    <div class="screen2 hide">
      <h2>Correct! You guessed it in <span id="attempts">1</span> attempt(s).</h2>
      <button id="btnReset">Play Again</button>
    </div>
  </main>

  <script src="./main.js"></script>
</body>

</html>

Create a JavaScript file (e.g., main.js) and include the following JavaScript code:

// Variables
let randomNumber = Math.round(Math.random() * 10);
const screen1 = document.querySelector('.screen1');
const screen2 = document.querySelector('.screen2');
const btnTry = document.querySelector("#btnTry");
const btnReset = document.querySelector("#btnReset");
let xAttempts = 1;

// Event Listeners
btnTry.addEventListener('click', handleTryClick);
btnReset.addEventListener('click', handleResetClick);
document.addEventListener('keydown', function (e) {
  if (e.key === 'Enter' && screen1.classList.contains('hide')) {
    handleResetClick();
  }
});

// Callback Functions
function handleTryClick(event) {
  event.preventDefault();

  const inputNumber = document.querySelector('#inputNumber');

  if (Number(inputNumber.value) === randomNumber) {
    toggleScreen();

    document.querySelector('.screen2 h2').innerText = `Correct! You guessed it in ${xAttempts} attempt(s).`;
  }

  xAttempts++;
}

function handleResetClick() {
  toggleScreen();
  xAttempts = 1;
  randomNumber = Math.round(Math.random() * 10);
}

function toggleScreen() {
  screen1.classList.toggle("hide");
  screen2.classList.toggle("hide");
}

Create a CSS file (e.g., style.css) and define the styling for the game interface. Customize the styles as desired.

Open the HTML file in a web browser to start playing the Guessing Game.

Usage
Open the HTML file in a web browser.
The game will display the instructions on the first screen (screen1), asking the player to guess a number between 0 and 10.
Enter a number in the input field and click the "Guess" button (btnTry).
If the guessed number matches the randomly generated number, the game will display the second screen (screen2) showing a success message with the number of attempts made. Otherwise, the player can keep guessing.
On the second screen, click the "Play Again" button (btnReset) to reset the game and go back to the first screen to play again.
License
This project is licensed under the MIT License.