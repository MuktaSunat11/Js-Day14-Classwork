# Stop Watch

This is a simple stopwatch built using HTML, CSS, and JavaScript.

The HTML file contains the basic structure of the stopwatch.

# Html
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Stop Watch</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

    <div id="timer">00:00:00</div>
    <div id="buttons">
        <button id="start">Start</button>
        <button id="stop">Stop</button>
        <button id="reset">Reset</button>
    </div>
    <script src="script.js"></script>
</body>
</html>
```
# Css
```
*{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  #timer {
    font-size: 7rem;
    font-weight: 700;
    text-shadow: 2px 2px #f8a5c2;
    color: #463bc5;
    width: 600px;
    text-align: center;
    margin: 40px auto;
  }
  
  #buttons {
    display: flex;
    justify-content: center;
  }
  
  button {
    background-color: #7c2fca;
    color: white;
    border: none;
    font-size: 2rem;
    font-weight: bold;
    padding: 1.5rem 4rem;
    margin: 1rem;
    border-radius: 30px;
    cursor: pointer;
    box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.3);
    transition: all 0.2s;
  }
  
  button:hover {
    background-color: #f44583;
    box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.5);
}
```
# Javascript
```
const timer = document.getElementById("timer");
const startButton = document.getElementById("start");
const stopButton = document.getElementById("stop");
const resetButton
 = document.getElementById("reset");

let startTime = 0;
let elapsedTime = 0;
let timerInterval;

function startTimer() {
  startTime = Date.now() - elapsedTime;

  timerInterval = setInterval(() => {
    elapsedTime = Date.now() - startTime;
    timer.textContent = formatTime(elapsedTime);
  }, 10);

  startButton.disabled = true;
  stopButton.disabled = false;
}

function formatTime(elapsedTime) {
  const milliseconds = Math.floor((elapsedTime % 1000) / 10);
  const seconds = Math.floor((elapsedTime % (1000 * 60)) / 1000);
  const minutes = Math.floor((elapsedTime % (1000 * 60 * 60)) / (1000 * 60));
  const hours = Math.floor(elapsedTime / (1000 * 60 * 60));
  return (
    (hours ? (hours > 9 ? hours : "0" + hours) : "00") +
    ":" +
    (minutes ? (minutes > 9 ? minutes : "0" + minutes) : "00") +
    ":" +
    (seconds ? (seconds > 9 ? seconds : "0" + seconds) : "00") +
    "." +
    (milliseconds > 9 ? milliseconds : "0" + milliseconds)
  );
}
function stopTimer() {
  clearInterval(timerInterval);
  startButton.disabled = false;
  stopButton.disabled = true;
}
function resetTimer() {
  clearInterval(timerInterval);

  elapsedTime = 0;
  timer.textContent = "00:00:00";

  startButton.disabled = false;
  stopButton.disabled = true;
}

startButton.addEventListener("click", startTimer);
stopButton.addEventListener("click", stopTimer);
resetButton
.addEventListener("click", resetTimer);
```
