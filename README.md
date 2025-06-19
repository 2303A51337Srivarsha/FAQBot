<!DOCTYPE html>
<html>
<head>
  <title>FAQBot</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f5f5f5;
      padding: 30px;
    }
    #chat {
      border: 1px solid #ccc;
      padding: 15px;
      height: 300px;
      overflow-y: auto;
      background: white;
    }
    #input-area {
      margin-top: 15px;
    }
    .message {
      margin-bottom: 10px;
    }
    .user {
      font-weight: bold;
      color: #007bff;
    }
    .bot {
      color: #333;
    }
  </style>
</head>
<body>
  <h1>FAQBot 🤖</h1>
  <div id="chat"></div>

  <div id="input-area">
    <input type="text" id="user-input" placeholder="Ask a question..." size="40" />
    <button onclick="handleUserInput()">Send</button>
  </div>

  <script>
    const faqs = {
      "what is your name": "I am FAQBot, your friendly assistant!",
      "how are you": "I'm doing great, thank you!",
      "what can you do": "I can answer some basic questions.",
      "who created you": "I was created using HTML and JavaScript!",
      "bye": "Goodbye! Have a nice day!"
    };

    function getAnswer(question) {
      question = question.toLowerCase().trim();
      return faqs[question] || "Sorry, I don't know the answer to that.";
    }

    function handleUserInput() {
      const input = document.getElementById('user-input');
      const question = input.value;
      if (question === "") return;

      appendMessage("You", question, "user");
      const answer = getAnswer(question);
      appendMessage("FAQBot", answer, "bot");
      input.value = "";
    }

    function appendMessage(sender, text, className) {
      const chat = document.getElementById('chat');
      const div = document.createElement('div');
      div.classList.add("message", className);
      div.innerHTML = <strong>${sender}:</strong> ${text};
      chat.appendChild(div);
      chat.scrollTop = chat.scrollHeight;
    }
  </script>
</body>
</html>
