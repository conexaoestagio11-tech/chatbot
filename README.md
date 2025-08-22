<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Chatbot Simples</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 0; padding: 0; }
    #chat-container {
      position: fixed;
      bottom: 20px;
      right: 20px;
      width: 320px;
      height: 450px;
      border-radius: 15px;
      background: #f5f5f5;
      display: flex;
      flex-direction: column;
      overflow: hidden;
      box-shadow: 0 4px 12px rgba(0,0,0,0.2);
    }
    #chat-header {
      background: #4CAF50;
      color: white;
      text-align: center;
      padding: 12px;
      font-weight: bold;
    }
    #chat-messages {
      flex: 1;
      padding: 10px;
      overflow-y: auto;
      font-size: 14px;
      display: flex;
      flex-direction: column;
    }
    .msg {
      max-width: 75%;
      padding: 8px 12px;
      margin: 6px 0;
      border-radius: 15px;
      line-height: 1.3;
      word-wrap: break-word;
    }
    .user {
      align-self: flex-end;
      background: #DCF8C6;
    }
    .bot {
      align-self: flex-start;
      background: #fff;
      border: 1px solid #ddd;
    }
    #chat-input {
      display: flex;
      border-top: 1px solid #ccc;
      background: #fff;
    }
    #chat-input input {
      flex: 1;
      padding: 10px;
      border: none;
      outline: none;
      font-size: 14px;
    }
    #chat-input button {
      padding: 10px 14px;
      border: none;
      background: #4CAF50;
      color: white;
      cursor: pointer;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <div id="chat-container">
    <div id="chat-header">🤖 Chatbot</div>
    <div id="chat-messages"></div>
    <div id="chat-input">
      <input type="text" id="user-input" placeholder="Digite aqui..." onkeypress="if(event.key==='Enter') sendMessage()">
      <button onclick="sendMessage()">➤</button>
    </div>
  </div>

  <script>
    const messages = document.getElementById("chat-messages");

    function sendMessage() {
      const input = document.getElementById("user-input");
      const text = input.value.trim();
      if (text === "") return;

      // Mostrar mensagem do usuário
      addMessage(text, "user");

      // Resposta do bot
      setTimeout(() => {
        let resposta = getBotResponse(text);
        addMessage(resposta, "bot");
      }, 500);

      input.value = "";
    }

    function addMessage(text, sender) {
      const msgDiv = document.createElement("div");
      msgDiv.classList.add("msg", sender);
      msgDiv.innerText = text;
      messages.appendChild(msgDiv);
      messages.scrollTop = messages.scrollHeight;
    }

    function getBotResponse(msg) {
      msg = msg.toLowerCase();
      if (msg.includes("oi") || msg.includes("olá")) return "Oi! Como posso ajudar?";
      if (msg.includes("bom dia")) return "Bom dia! Espero que tenha um ótimo dia 🌞";
      if (msg.includes("boa tarde")) return "Boa tarde! Como você está?";
      if (msg.includes("boa noite")) return "Boa noite! Desejo um descanso tranquilo 🌙";
      if (msg.includes("ajuda") || msg.includes("o que você faz")) return "Sou um bot simples, posso responder cumprimentos e dúvidas básicas.";
      return "Desculpe, não entendi 🤔";
    }
  </script>
</body>
</html>
