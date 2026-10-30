# jarvis
<!DOCTYPE html>  <html lang="en">  
<head>  
<meta charset="UTF-8">  
<meta name="viewport" content="width=device-width, initial-scale=1.0">  
<title>JARVIS AI</title>  <style>  
* {  
  box-sizing: border-box;  
}  
  
body {  
  margin: 0;  
  background: #050b16;  
  color: #e7f8ff;  
  font-family: Arial, sans-serif;  
  text-align: center;  
}  
  
header {  
  padding: 24px 10px;  
  letter-spacing: 5px;  
  color: #35d9ff;  
}  
  
.status {  
  color: #58f5a5;  
  font-size: 12px;  
}  
  
.circle {  
  width: 185px;  
  height: 185px;  
  border: 3px solid #22cfff;  
  border-radius: 50%;  
  margin: 35px auto;  
  display: flex;  
  justify-content: center;  
  align-items: center;  
  box-shadow: 0 0 25px #087cae;  
  font-size: 55px;  
}  
  
h2 {  
  color: #36d9ff;  
}  
  
#chat {  
  margin: 20px auto;  
  padding: 12px;  
  width: 90%;  
  max-width: 450px;  
  height: 180px;  
  overflow-y: auto;  
  text-align: left;  
  background: #101c2d;  
  border-radius: 12px;  
}  
  
input {  
  width: 65%;  
  padding: 13px;  
  border-radius: 20px;  
  border: 1px solid #20bce8;  
  background: #101c2d;  
  color: white;  
}  
  
button {  
  padding: 12px 17px;  
  margin: 6px;  
  border: none;  
  border-radius: 20px;  
  background: #087fae;  
  color: white;  
  font-weight: bold;  
}  
  
button:active {  
  background: #16bce9;  
}  
  
footer {  
  margin: 25px;  
  color: #69869d;  
  font-size: 12px;  
}  
</style>  </head>  <body>  <header>  
  <h1>J.A.R.V.I.S</h1>  
  <div class="status">● SYSTEM ONLINE</div>  
</header>  <div class="circle">◉</div>  <h2>PERSONAL AI ASSISTANT</h2>  
<p id="status">Awaiting your command...</p>  <div id="chat">  
  <p><b>JARVIS:</b> Hello! Systems are ready.</p>  
</div>  <input id="message" placeholder="Type a command...">  
<button onclick="sendMessage()">SEND</button>  
<br>  
<button onclick="listen()">🎙 SPEAK</button>  <footer>  
  JARVIS AI | VERSION 1.0  
</footer>  <script>  
function openWebSearch(query) {  
    if (!query.trim()) {  
        return "Please tell me what to search.";  
    }  
  
    const url =  
        "https://www.google.com/search?q=" +  
        encodeURIComponent(query);  
  
    window.open(url, "_blank");  
  
    return "Searching the internet for " + query;  
}  
  
function reply(text) {  
  const chat = document.getElementById("chat");  
  
  const message = document.createElement("p");  
  const label = document.createElement("b");  
  
  label.textContent = "JARVIS: ";  
  message.appendChild(label);  
  message.appendChild(document.createTextNode(text));  
  
  chat.appendChild(message);  
  chat.scrollTop = chat.scrollHeight;  
  
  const speech = new SpeechSynthesisUtterance(text);  
  speech.lang = "en-IN";  
  speechSynthesis.speak(speech);  
}  
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
  
  if (command.startsWith("search ")) {  
    const query = original.substring(7).trim();  
    reply(openWebSearch(query));  
  }  
  else if (command.includes("hello")) {  
    reply("Hello! How can I assist you?");  
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
    reply("Try hello, time, date, status or search followed by a topic.");  
  }  
  else {  
    reply("I don't know that command yet. I am still learning.");  
  }  
  
  chat.scrollTop = chat.scrollHeight;  
}  
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
  
  recognition.start();  
}  
</script>  </body>  
</html>  