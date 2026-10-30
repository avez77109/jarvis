
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="theme-color" content="#050b16">
<title>J.A.R.V.I.S 3.0</title>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  min-height: 100vh;
  background: radial-gradient(circle, #10263b, #030711 75%);
  color: #e7f8ff;
  font-family: Arial, sans-serif;
  text-align: center;
}

header {
  padding: 22px 10px;
  letter-spacing: 5px;
  color: #35d9ff;
  text-shadow: 0 0 15px #087cae;
}

.status {
  color: #58f5a5;
  font-size: 12px;
  letter-spacing: 2px;
}

.circle {
  width: 175px;
  height: 175px;
  border: 3px solid #22cfff;
  border-radius: 50%;
  margin: 25px auto;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 65px;
  color: #35d9ff;
  box-shadow: 0 0 20px #087cae,
              inset 0 0 25px #087cae;
  animation: pulse 3s infinite;
}

@keyframes pulse {
  50% {
    box-shadow: 0 0 40px #22cfff,
                inset 0 0 35px #087cae;
  }
}

h2 {
  color: #36d9ff;
  letter-spacing: 3px;
}

#status {
  color: #58f5a5;
  font-size: 13px;
}

#chat {
  margin: 20px auto;
  padding: 15px;
  width: 90%;
  max-width: 500px;
  height: 250px;
  overflow-y: auto;
  overflow-wrap: anywhere;
  text-align: left;
  background: rgba(16, 28, 45, 0.9);
  border: 1px solid #176c91;
  border-radius: 12px;
  box-shadow: 0 0 15px #087cae33;
}

#chat p {
  line-height: 1.5;
}

#chat b {
  color: #35d9ff;
}

.controls {
  width: 95%;
  max-width: 550px;
  margin: auto;
}

input {
  width: 65%;
  padding: 13px;
  border-radius: 20px;
  border: 1px solid #20bce8;
  background: #101c2d;
  color: white;
  outline: none;
}

button {
  padding: 12px 17px;
  margin: 6px;
  border: 1px solid #22cfff;
  border-radius: 20px;
  background: #087fae;
  color: white;
  font-weight: bold;
  cursor: pointer;
}

button:active {
  background: #16bce9;
}

.commands {
  margin: 25px auto;
  width: 90%;
  max-width: 500px;
  padding: 15px;
  border: 1px solid #176c91;
  border-radius: 12px;
  background: #101c2d;
  font-size: 13px;
  line-height: 1.8;
}

.commands h3 {
  color: #35d9ff;
}

footer {
  margin: 25px;
  color: #69869d;
  font-size: 12px;
}

@media(max-width: 420px) {
  input {
    width: 62%;
  }

  .circle {
    width: 145px;
    height: 145px;
  }
}
</style>
</head>

<body>

<header>
  <h1>J.A.R.V.I.S</h1>
  <div class="status">● SYSTEM ONLINE | VERSION 3.0</div>
</header>

<div class="circle">◉</div>

<h2>PERSONAL AI ASSISTANT</h2>
<p id="status">Awaiting your command...</p>

<div id="chat">
  <p><b>JARVIS:</b> Hello! All basic systems are ready.</p>
</div>

<div class="controls">
  <input
    id="message"
    placeholder="Type your command..."
    autocomplete="off"
  >
  <button onclick="sendMessage()">SEND</button>
  <br>
  <button onclick="listen()">🎙 SPEAK</button>
  <button onclick="stopSpeaking()">🔇 STOP VOICE</button>
</div>

<div class="commands">
  <h3>AVAILABLE COMMANDS</h3>
  Hello | Your name | Time | Date | Status<br>
  Search Mumbai | Wikipedia Tesla | Weather Mumbai<br>
  Calculate 25*4 | Help
</div>

<footer>
  JARVIS AI | VERSION 3.0
</footer>

<script>

// GOOGLE SEARCH
function openWebSearch(query) {
  if (!query.trim()) {
    return "Please tell me what to search.";
  }

  window.open(
    "https://www.google.com/search?q=" +
    encodeURIComponent(query),
    "_blank"
  );

  return "Searching the internet for " + query;
}


// JARVIS RESPONSE
function reply(text) {
  const chat = document.getElementById("chat");

  const message = document.createElement("p");
  const label = document.createElement("b");

  label.textContent = "JARVIS: ";
  message.appendChild(label);
  message.appendChild(document.createTextNode(text));

  chat.appendChild(message);
  chat.scrollTop = chat.scrollHeight;

  if ("speechSynthesis" in window) {
    speechSynthesis.cancel();

    const speech = new SpeechSynthesisUtterance(text);
    speech.lang = "en-IN";
    speech.rate = 1;

    speechSynthesis.speak(speech);
  }
}


// STOP VOICE
function stopSpeaking() {
  if ("speechSynthesis" in window) {
    speechSynthesis.cancel();
  }

  document.getElementById("status").innerText =
    "Voice stopped.";
}


// SAFE CALCULATOR
function calculate(expression) {
  const clean = expression.replace(/\s/g, "");

  const tokens = clean.match(
    /\d*\.?\d+|[()+\-*/%]/g
  );

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
  const input = document.getElementById("message");
  const original = input.value.trim();
  const command = original.toLowerCase();

  if (!command) return;

  const chat = document.getElementById("chat");

  const userMessage = document.createElement("p");
  const userLabel = document.createElement("b");

  userLabel.textContent = "YOU: ";
  userMessage.appendChild(userLabel);
  userMessage.appendChild(
    document.createTextNode(original)
  );

  chat.appendChild(userMessage);
  input.value = "";

  if (command.startsWith("calculate ")) {
    const expression = original.substring(10).trim();

    try {
      const result = calculate(expression);
      reply("The answer is " + result);
    } catch (error) {
      reply("Please enter a valid calculation.");
    }
  }

  else if (command.startsWith("wikipedia ")) {
    const topic = original.substring(10).trim();

    if (topic) {
      window.open(
        "https://en.wikipedia.org/w/index.php?search=" +
        encodeURIComponent(topic),
        "_blank"
      );

      reply("Searching Wikipedia for " + topic);
    } else {
      reply("Please tell me a Wikipedia topic.");
    }
  }

  else if (command.startsWith("weather ")) {
    const city = original.substring(8).trim();

    if (city) {
      window.open(
        "https://www.google.com/search?q=" +
        encodeURIComponent("weather in " + city),
        "_blank"
      );

      reply("Checking the weather for " + city);
    } else {
      reply("Please tell me a city.");
    }
  }

  else if (command.startsWith("search ")) {
    const query = original.substring(7).trim();
    reply(openWebSearch(query));
  }

  else if (
    command.includes("hello") ||
    command.includes("hey")
  ) {
    reply("Hello! JARVIS is ready to assist you.");
  }

  else if (command.includes("your name")) {
    reply("I am JARVIS, your personal assistant.");
  }

  else if (command.includes("time")) {
    reply("The time is " +
      new Date().toLocaleTimeString());
  }

  else if (command.includes("date")) {
    reply("Today's date is " +
      new Date().toLocaleDateString());
  }

  else if (command.includes("status")) {
    reply("All basic systems are operational.");
  }

  else if (command.includes("help")) {
    reply(
      "You can ask for time, date, status, " +
      "search, Wikipedia, weather or calculations."
    );
  }

  else if (
    command.startsWith("who is ") ||
    command.startsWith("what is ") ||
    command.startsWith("where is ") ||
    command.startsWith("why ") ||
    command.startsWith("how ") ||
    command.startsWith("when ")
  ) {
    reply("Let me search for that information.");
    openWebSearch(original);
  }

  else {
    reply(
      "I don't understand that command yet. " +
      "Try saying help or search followed by a topic."
    );
  }

  chat.scrollTop = chat.scrollHeight;
}


// PRESS ENTER TO SEND
document.getElementById("message")
  .addEventListener("keydown", function(event) {
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
    document.getElementById("status").innerText =
      "Speech recognition is not supported. Try Chrome.";
    return;
  }

  const recognition = new Recognition();

  recognition.lang = "en-IN";
  recognition.interimResults = false;
  recognition.maxAlternatives = 1;

  recognition.onstart = function() {
    document.getElementById("status").innerText =
      "Listening...";
  };

  recognition.onresult = function(event) {
    document.getElementById("message").value =
      event.results[0][0].transcript;

    sendMessage();
  };

  recognition.onerror = function(event) {
    document.getElementById("status").innerText =
      "Voice error: " + event.error;
  };

  recognition.onend = function() {
    document.getElementById("status").innerText =
      "Awaiting your command...";
  };

  try {
    recognition.start();
  } catch (error) {
    document.getElementById("status").innerText =
      "Please try speaking again.";
  }
}

</script>

</body>
</html>
