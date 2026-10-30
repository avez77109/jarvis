
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="theme-color" content="#050b16">
<title>J.A.R.V.I.S 4.0</title>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  min-height: 100vh;
  background: radial-gradient(circle at center, #102c46, #030711 75%);
  color: #e7f8ff;
  font-family: Arial, sans-serif;
  text-align: center;
}

header {
  padding: 22px 10px;
  color: #35d9ff;
  letter-spacing: 5px;
  text-shadow: 0 0 15px #087cae;
}

header h1 {
  margin-bottom: 8px;
}

.status {
  color: #58f5a5;
  font-size: 12px;
  letter-spacing: 2px;
}

.circle {
  width: 175px;
  height: 175px;
  margin: 25px auto;
  display: flex;
  justify-content: center;
  align-items: center;
  border: 3px solid #22cfff;
  border-radius: 50%;
  color: #35d9ff;
  font-size: 65px;
  box-shadow: 0 0 25px #087cae,
              inset 0 0 25px #087cae;
  animation: pulse 3s infinite;
}

.circle.listening {
  border-color: #58f5a5;
  box-shadow: 0 0 40px #58f5a5,
              inset 0 0 25px #58f5a5;
}

@keyframes pulse {
  50% {
    box-shadow: 0 0 45px #22cfff,
                inset 0 0 35px #087cae;
  }
}

h2 {
  color: #36d9ff;
  letter-spacing: 2px;
}

#status {
  color: #58f5a5;
  font-size: 13px;
}

#chat {
  width: 92%;
  max-width: 520px;
  height: 300px;
  margin: 20px auto;
  padding: 15px;
  overflow-y: auto;
  overflow-wrap: anywhere;
  text-align: left;
  background: rgba(10, 25, 42, 0.95);
  border: 1px solid #176c91;
  border-radius: 14px;
  box-shadow: 0 0 18px #087cae33;
}

#chat p {
  line-height: 1.5;
  margin: 12px 0;
}

#chat b {
  color: #35d9ff;
}

#chat a {
  color: #58f5a5;
  overflow-wrap: anywhere;
}

.controls {
  width: 95%;
  max-width: 550px;
  margin: auto;
}

input {
  width: 68%;
  padding: 14px;
  border: 1px solid #20bce8;
  border-radius: 25px;
  outline: none;
  background: #101c2d;
  color: white;
  font-size: 14px;
}

input:focus {
  box-shadow: 0 0 12px #087cae;
}

button {
  padding: 12px 17px;
  margin: 6px 3px;
  border: 1px solid #22cfff;
  border-radius: 22px;
  background: #087fae;
  color: white;
  font-weight: bold;
  cursor: pointer;
}

button:active {
  background: #16bce9;
}

.secondary {
  background: #14283b;
}

.danger {
  border-color: #ff6375;
  background: #652b3b;
}

.commands {
  width: 90%;
  max-width: 520px;
  margin: 25px auto;
  padding: 16px;
  border: 1px solid #176c91;
  border-radius: 14px;
  background: #101c2d;
  font-size: 13px;
  line-height: 2;
}

.commands h3 {
  color: #35d9ff;
}

footer {
  margin: 25px;
  padding-bottom: 15px;
  color: #69869d;
  font-size: 12px;
}

@media(max-width: 420px) {
  .circle {
    width: 145px;
    height: 145px;
  }

  input {
    width: 64%;
  }

  button {
    padding: 11px 13px;
  }
}
</style>
</head>

<body>

<header>
  <h1>J.A.R.V.I.S</h1>
  <div class="status">● SYSTEM ONLINE | VERSION 4.0</div>
</header>

<div class="circle" id="core">◉</div>

<h2>PERSONAL AI ASSISTANT</h2>
<p id="status">Awaiting your command...</p>

<div id="chat" aria-live="polite">
  <p><b>JARVIS:</b> Good day! All systems are ready. How may I assist you?</p>
</div>

<div class="controls">

  <input
    id="message"
    type="text"
    placeholder="Type your command..."
    autocomplete="off"
  >

  <button onclick="sendMessage()">SEND</button>

  <br>

  <button onclick="listen()">🎙 SPEAK</button>

  <button class="secondary" onclick="stopSpeaking()">
    🔇 STOP VOICE
  </button>

  <button class="danger" onclick="clearChat()">
    CLEAR CHAT
  </button>

</div>

<div class="commands">
  <h3>JARVIS COMMAND CENTER</h3>

  Hello | Hey JARVIS | Your name<br>
  Time | Date | Status | Help<br>
  Calculate 25*4<br>
  Search Mumbai<br>
  Wikipedia Tesla<br>
  Weather Mumbai<br>
  Who is Elon Musk?
</div>

<footer>
  J.A.R.V.I.S 4.0 | SMART ASSISTANT INTERFACE
  <br>
  Built with HTML, CSS and JavaScript
</footer>

<script>

// ELEMENTS
const chat = document.getElementById("chat");
const input = document.getElementById("message");
const statusText = document.getElementById("status");
const core = document.getElementById("core");


// ADD MESSAGE
function addMessage(sender, text) {

  const message = document.createElement("p");
  const label = document.createElement("b");

  label.textContent = sender + ": ";

  message.appendChild(label);
  message.appendChild(document.createTextNode(text));

  chat.appendChild(message);

  chat.scrollTop = chat.scrollHeight;
}


// ADD CLICKABLE SEARCH LINK
function addSearchLink(title, url) {

  const message = document.createElement("p");
  const label = document.createElement("b");
  const link = document.createElement("a");

  label.textContent = "JARVIS: ";
  link.textContent = title;
  link.href = url;
  link.target = "_blank";
  link.rel = "noopener noreferrer";

  message.appendChild(label);
  message.appendChild(link);

  chat.appendChild(message);
  chat.scrollTop = chat.scrollHeight;
}


// SPEAK RESPONSE
function speak(text) {

  if (!("speechSynthesis" in window)) {
    return;
  }

  speechSynthesis.cancel();

  const speech = new SpeechSynthesisUtterance(text);

  speech.lang = "en-IN";
  speech.rate = 1;
  speech.pitch = 1;

  speech.onstart = function() {
    statusText.textContent = "JARVIS is speaking...";
  };

  speech.onend = function() {
    statusText.textContent = "Awaiting your command...";
  };

  speechSynthesis.speak(speech);
}


// JARVIS RESPONSE
function reply(text) {

  addMessage("JARVIS", text);
  speak(text);

}


// STOP SPEECH
function stopSpeaking() {

  if ("speechSynthesis" in window) {
    speechSynthesis.cancel();
  }

  statusText.textContent = "Voice stopped.";
}


// CLEAR CHAT
function clearChat() {

  stopSpeaking();

  chat.innerHTML = "";

  addMessage(
    "JARVIS",
    "Conversation cleared. Systems are ready."
  );

}


// GOOGLE SEARCH
function searchGoogle(query) {

  const url =
    "https://www.google.com/search?q=" +
    encodeURIComponent(query);

  addSearchLink("Open Google results for " + query, url);

}


// WIKIPEDIA SEARCH
function searchWikipedia(topic) {

  const url =
    "https://en.wikipedia.org/w/index.php?search=" +
    encodeURIComponent(topic);

  addSearchLink("Open Wikipedia results for " + topic, url);

}


// WEATHER SEARCH
function searchWeather(city) {

  const url =
    "https://www.google.com/search?q=" +
    encodeURIComponent("weather in " + city);

  addSearchLink("Check weather for " + city, url);

}


// SAFE CALCULATOR
function calculate(expression) {

  const clean = expression.replace(/\s/g, "");

  const tokens = clean.match(/\d*\.?\d+|[()+\-*/%]/g);

  if (!tokens || tokens.join("") !== clean) {
    throw new Error("Invalid calculation");
  }

  let position = 0;

  function factor() {

    const token = tokens[position++];

    if (token === "+") return factor();
    if (token === "-") return -factor();

    if (token === "(") {

      const value = sum();

      if (tokens[position++] !== ")") {
        throw new Error("Missing bracket");
      }

      return value;
    }

    const number = Number(token);

    if (!Number.isFinite(number)) {
      throw new Error("Invalid number");
    }

    return number;
  }

  function term() {

    let value = factor();

    while (
      tokens[position] === "*" ||
      tokens[position] === "/" ||
      tokens[position] === "%"
    ) {

      const operator = tokens[position++];
      const next = factor();

      if (
        (operator === "/" || operator === "%") &&
        next === 0
      ) {
        throw new Error("Cannot divide by zero");
      }

      if (operator === "*") value *= next;
      if (operator === "/") value /= next;
      if (operator === "%") value %= next;

    }

    return value;
  }

  function sum() {

    let value = term();

    while (
      tokens[position] === "+" ||
      tokens[position] === "-"
    ) {

      const operator = tokens[position++];
      const next = term();

      if (operator === "+") value += next;
      if (operator === "-") value -= next;

    }

    return value;
  }

  const result = sum();

  if (
    position !== tokens.length ||
    !Number.isFinite(result)
  ) {
    throw new Error("Invalid calculation");
  }

  return result;
}


// MAIN COMMAND SYSTEM
function sendMessage() {

  const original = input.value.trim();
  const command = original.toLowerCase();

  if (!command) return;

  stopSpeaking();

  addMessage("YOU", original);

  input.value = "";

  // GREETINGS
  if (
    command.includes("hello") ||
    command.includes("hey") ||
    command.includes("good morning") ||
    command.includes("good evening")
  ) {

    reply("Hello! JARVIS is ready. What can I do for you?");

  }

  // NAME
  else if (command.includes("your name")) {

    reply("I am JARVIS, your personal smart assistant.");

  }

  // TIME
  else if (command.includes("time")) {

    reply("The current time is " +
      new Date().toLocaleTimeString("en-IN"));

  }

  // DATE
  else if (command.includes("date")) {

    reply("Today's date is " +
      new Date().toLocaleDateString("en-IN"));

  }

  // STATUS
  else if (command.includes("status")) {

    reply("All basic systems are operational. Voice and command systems are ready.");

  }

  // CALCULATOR
  else if (command.startsWith("calculate ")) {

    const expression = original.substring(10).trim();

    try {

      const result = calculate(expression);

      reply("The answer is " + result);

    } catch (error) {

      reply("Please enter a valid calculation.");

    }

  }

  // WIKIPEDIA
  else if (command.startsWith("wikipedia ")) {

    const topic = original.substring(10).trim();

    if (topic) {

      reply("I found a Wikipedia search for " + topic);
      searchWikipedia(topic);

    } else {

      reply("Please tell me a topic.");

    }

  }

  // WEATHER
  else if (command.startsWith("weather ")) {

    const city = original.substring(8).trim();

    if (city) {

      reply("Here is a weather search for " + city);
      searchWeather(city);

    } else {

      reply("Please tell me a city.");

    }

  }

  // GOOGLE SEARCH
  else if (command.startsWith("search ")) {

    const query = original.substring(7).trim();

    if (query) {

      reply("Here are your Google search results.");
      searchGoogle(query);

    } else {

      reply("Please tell me what to search.");

    }

  }

  // HELP
  else if (command.includes("help")) {

    reply("Try hello, time, date, status, calculate, search, Wikipedia or weather.");

  }

  // GENERAL QUESTIONS: SEARCH THE WEB
  else if (
    command.startsWith("who is ") ||
    command.startsWith("what is ") ||
    command.startsWith("where is ") ||
    command.startsWith("why ") ||
    command.startsWith("how ") ||
    command.startsWith("when ")
  ) {

    reply("I can help you look that up. Here are some search results.");

    searchGoogle(original);

  }

  // UNKNOWN COMMAND
  else {

    reply("I don't know that command yet. Type help to see what I can do.");

  }

}


// ENTER TO SEND
input.addEventListener("keydown", function(event) {

  if (event.key === "Enter") {
    sendMessage();
  }

});


// VOICE RECOGNITION
function listen() {

  const Recognition =
    window.SpeechRecognition ||
    window.webkitSpeechRecognition;

  if (!Recognition) {

    statusText.textContent =
      "Voice recognition is not supported. Try Chrome.";

    return;

  }

  const recognition = new Recognition();

  recognition.lang = "en-IN";
  recognition.interimResults = false;
  recognition.maxAlternatives = 1;

  recognition.onstart = function() {

    statusText.textContent = "Listening...";
    core.classList.add("listening");

  };

  recognition.onresult = function(event) {

    const spokenText =
      event.results[0][0].transcript;

    input.value = spokenText;

    sendMessage();

  };

  recognition.onerror = function(event) {

    statusText.textContent =
      "Voice error: " + event.error;

  };

  recognition.onend = function() {

    core.classList.remove("listening");

    if (statusText.textContent === "Listening...") {
      statusText.textContent = "Awaiting your command...";
    }

  };

  try {

    recognition.start();

  } catch (error) {

    statusText.textContent =
      "Please try speaking again.";

  }

}

</script>

</body>
</html>
