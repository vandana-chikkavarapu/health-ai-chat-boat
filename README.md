<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Health AI Chatbot</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f0f8ff;
      margin: 0;
      padding: 0;
    }
    .chat-container {
      max-width: 600px;
      margin: 40px auto;
      background: white;
      border-radius: 10px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
      overflow: hidden;
    }
    .chat-header {
      background: #007acc;
      color: white;
      text-align: center;
      padding: 20px;
      font-size: 1.5em;
    }
    .chat-box {
      height: 400px;
      overflow-y: auto;
      padding: 20px;
      border-bottom: 1px solid #ddd;
    }
    .chat-message {
      margin: 10px 0;
    }
    .chat-message.user {
      text-align: right;
      color: #333;
    }
    .chat-message.bot {
      text-align: left;
      color: #007acc;
    }
    .chat-input {
      display: flex;
      border-top: 1px solid #ccc;
    }
    .chat-input input {
      flex: 1;
      padding: 15px;
      border: none;
      font-size: 1em;
    }
    .chat-input button {
      padding: 15px;
      background: #007acc;
      color: white;
      border: none;
      cursor: pointer;
    }
    .chat-input button:hover {
      background: #005f99;
    }
  </style>
</head>
<body>

<div class="chat-container">
  <div class="chat-header">Health AI Chatbot</div>
  <div class="chat-box" id="chatBox"></div>
  <div class="chat-input">
    <input type="text" id="userInput" placeholder="Type your health question..." />
    <button onclick="sendMessage()">Send</button>
  </div>
</div>

<script>
  function sendMessage() {
    const input = document.getElementById('userInput');
    const chatBox = document.getElementById('chatBox');
    const userText = input.value.trim();
    if (!userText) return;

    // Add user message
    chatBox.innerHTML += `<div class="chat-message user"><strong>You:</strong> ${userText}</div>`;

    // Bot response
    const botText = getBotReply(userText);
    chatBox.innerHTML += `<div class="chat-message bot"><strong>Bot:</strong> ${botText}</div>`;

    input.value = '';
    chatBox.scrollTop = chatBox.scrollHeight;
  }

  function getBotReply(input) {
    const msg = input.toLowerCase();
    if (msg.includes("fever")) {
      return "You may have an infection. Rest, stay hydrated, and monitor your temperature.";
    } else if (msg.includes("headache")) {
      return "Try to rest, reduce screen time, and drink water. See a doctor if it persists.";
    } else if (msg.includes("cold")) {
      return "Rest, stay warm, and drink fluids. If symptoms worsen, consult a doctor.";
    } else if (msg.includes("covid")) {
      return "Isolate, monitor your symptoms, and get tested. Contact health services if needed.";
    } else if (msg.includes("stomach")) {
      return "Eat light foods, stay hydrated, and avoid spicy meals. Consult a doctor if pain continues.";
    } else {
      return "I'm here to help with health questions. Can you provide more details?";
    }
  }
</script>

</body>
</html>
