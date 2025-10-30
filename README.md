# Skibidi
Ok 😎, voici une description simple et prête à copier-coller pour ton dépôt GitHub :  “WawaBot : un mini-chat interactif où mes potes peuvent poser des questions et recevoir des réponses. Tu peux répondre toi-même ou activer le mode IA pour que le chat réponde automatiquement.”  
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>WawaBot Chat</title>
<style>
  body { font-family: Arial; background:#1a1a1a; color:#fff; display:flex; flex-direction:column; align-items:center; padding:20px;}
  #chat { width:100%; max-width:400px; height:500px; background:#222; overflow-y:scroll; padding:10px; border-radius:10px; margin-bottom:10px;}
  .message { margin:5px 0; padding:8px 12px; border-radius:8px; max-width:80%; }
  .user { background:#0a84ff; align-self:flex-end; }
  .bot { background:#444; align-self:flex-start; }
  #inputArea { display:flex; width:100%; max-width:400px; }
  #inputArea input { flex:1; padding:10px; border-radius:5px 0 0 5px; border:none; }
  #inputArea button { padding:10px; border:none; background:#0a84ff; color:#fff; border-radius:0 5px 5px 0; cursor:pointer; }
  #modeButton { margin-bottom:10px; padding:10px 15px; border:none; border-radius:5px; cursor:pointer; background:#0a84ff; color:#fff;}
</style>
</head>
<body>

<h2>WawaBot Chat</h2>
<button id="modeButton" onclick="toggleMode()">Mode IA : OFF</button>
<div id="chat"></div>

<div id="inputArea">
  <input type="text" id="userInput" placeholder="Pose ta question...">
  <button onclick="sendMessage()">Envoyer</button>
</div>

<script>
let iaMode = false;
const chat = document.getElementById('chat');
const modeButton = document.getElementById('modeButton');

function toggleMode(){
  iaMode = !iaMode;
  modeButton.textContent = "Mode IA : " + (iaMode ? "ON" : "OFF");
}

function sendMessage() {
  const input = document.getElementById('userInput');
  const text = input.value.trim();
  if(text === "") return;

  // Message de l'utilisateur
  const userMsg = document.createElement('div');
  userMsg.classList.add('message','user');
  userMsg.textContent = text;
  chat.appendChild(userMsg);
  chat.scrollTop = chat.scrollHeight;
  input.value = '';

  // Réponse
  setTimeout(() => {
    const botMsg = document.createElement('div');
    botMsg.classList.add('message','bot');
    
    if(iaMode){
      const responses = [
        "Hmm, c'est intéressant ! 😏",
        "Je vois… peux-tu m'en dire plus ?",
        "Ah oui, je comprends ce que tu veux dire.",
        "Intéressant ! Continue…",
        "D'accord, je note ça."
      ];
      botMsg.textContent = responses[Math.floor(Math.random()*responses.length)];
    } else {
      botMsg.textContent = "Réponse ici par toi-même 😎";
    }

    chat.appendChild(botMsg);
    chat.scrollTop = chat.scrollHeight;
  }, 500);
}
</script>

</body>
</html>
