<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Gazali AI - Intelligent Assistant</title>
  <link href="https://fonts.googleapis.com/css2?family=Anek+Latin:wght@300;400;500;600;700&family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet">
  <style>
    :root {
      --navy: #0a1128;
      --copper: #b87333;
      --copper-light: #ffb67f;
      --gold: #FFD700;
      --silver: #C0C0C0;
      --white: #ffffff;
      --gray: #e0e0e0;
      --shadow: 0 4px 25px rgba(0, 0, 0, 0.35);
      --radius: 12px;
      font-family: 'Poppins', sans-serif;
    }

    body {
      margin: 0;
      background: linear-gradient(135deg, var(--navy) 70%, var(--copper) 30%);
      color: var(--white);
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      text-align: center;
      padding: 20px;
    }

    .container {
      background: rgba(255,255,255,0.05);
      border-radius: var(--radius);
      box-shadow: var(--shadow);
      padding: 40px;
      max-width: 850px;
      width: 95%;
      backdrop-filter: blur(15px);
      position: relative;
    }

    .logo-container {
      position: relative;
      width: 140px;
      height: 140px;
      margin: 0 auto 25px;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .logo-base {
      width: 120px;
      height: 120px;
      border-radius: 50%;
      background: radial-gradient(circle at 30% 30%, var(--copper), var(--copper-light));
      position: absolute;
      box-shadow: 0 0 30px rgba(255,182,127,0.6), 0 6px 20px rgba(184,115,51,0.4);
      display: flex;
      justify-content: center;
      align-items: center;
      overflow: hidden;
    }

    .logo-brain {
      position: absolute;
      width: 80px;
      height: 60px;
      background: 
        radial-gradient(circle at 20px 25px, var(--gold) 8px, transparent 8px),
        radial-gradient(circle at 60px 25px, var(--gold) 8px, transparent 8px);
      border-radius: 40px 40px 50px 50px;
      box-shadow: 
        0 5px 15px rgba(255,215,0,0.4),
        inset 0 -5px 10px rgba(184,115,51,0.3);
      z-index: 2;
    }

    .logo-brain:before {
      content: '';
      position: absolute;
      width: 70px;
      height: 40px;
      top: 10px;
      left: 5px;
      border-radius: 35px 35px 45px 45px;
      background: linear-gradient(to bottom, transparent 60%, rgba(255,215,0,0.3) 100%);
    }

    .logo-connections {
      position: absolute;
      width: 100px;
      height: 100px;
      z-index: 1;
    }

    .connection {
      position: absolute;
      background: var(--silver);
      border-radius: 2px;
      opacity: 0.8;
    }

    .connection-1 {
      width: 40px;
      height: 3px;
      top: 30px;
      left: 20px;
      transform: rotate(45deg);
      box-shadow: 0 0 8px rgba(192,192,192,0.7);
    }

    .connection-2 {
      width: 40px;
      height: 3px;
      top: 30px;
      right: 20px;
      transform: rotate(-45deg);
      box-shadow: 0 0 8px rgba(192,192,192,0.7);
    }

    .connection-3 {
      width: 3px;
      height: 40px;
      bottom: 20px;
      left: 50%;
      transform: translateX(-50%);
      box-shadow: 0 0 8px rgba(192,192,192,0.7);
    }

    .logo-sparkles {
      position: absolute;
      width: 100%;
      height: 100%;
      z-index: 3;
    }

    .sparkle {
      position: absolute;
      width: 4px;
      height: 4px;
      background: var(--gold);
      border-radius: 50%;
      animation: sparkle 3s infinite;
    }

    .sparkle-1 {
      top: 15px;
      left: 25px;
      animation-delay: 0s;
    }

    .sparkle-2 {
      top: 20px;
      right: 30px;
      animation-delay: 0.5s;
    }

    .sparkle-3 {
      bottom: 25px;
      left: 35px;
      animation-delay: 1s;
    }

    .sparkle-4 {
      bottom: 30px;
      right: 25px;
      animation-delay: 1.5s;
    }

    @keyframes sparkle {
      0%, 100% { opacity: 0; transform: scale(0); }
      50% { opacity: 1; transform: scale(1.5); }
    }

    .logo-glow {
      position: absolute;
      width: 140px;
      height: 140px;
      border-radius: 50%;
      background: radial-gradient(circle, rgba(255,182,127,0.3) 0%, rgba(184,115,51,0.1) 70%, transparent 100%);
      animation: pulse 4s infinite;
      z-index: 0;
    }

    @keyframes pulse {
      0%, 100% { transform: scale(1); opacity: 0.7; }
      50% { transform: scale(1.1); opacity: 0.9; }
    }

    h1 {
      font-size: 2.8em;
      color: var(--copper-light);
      margin-bottom: 10px;
      text-shadow: 0 2px 10px rgba(255,182,127,0.3);
    }

    p {
      color: var(--gray);
      font-size: 1.2em;
      margin-bottom: 25px;
    }

    .options { 
      display: flex; 
      flex-wrap: wrap; 
      gap: 12px; 
      justify-content: center; 
      margin-bottom: 25px; 
    }
    
    .options button { 
      flex: 1 1 calc(33.333% - 12px); 
      min-width: 150px;
      padding: 14px; 
      border: none; 
      border-radius: var(--radius); 
      background: linear-gradient(135deg, var(--copper), var(--copper-light)); 
      color: var(--navy); 
      cursor: pointer; 
      font-weight: 700; 
      transition: transform 0.2s, box-shadow 0.3s; 
      font-family: 'Poppins', sans-serif;
    }
    
    .options button:hover { 
      transform: translateY(-3px); 
      box-shadow: 0 6px 18px rgba(255,182,127,0.5); 
    }

    .input-group { 
      display: flex; 
      gap: 12px; 
      margin-bottom: 25px; 
    }
    
    input[type="text"] { 
      flex-grow: 1; 
      padding: 14px; 
      border-radius: var(--radius); 
      border: none; 
      outline: none; 
      font-size: 1.05em; 
      color: var(--navy); 
      background: rgba(255,255,255,0.9);
      font-family: 'Anek Latin', sans-serif;
      font-weight: 500;
    }
    
    input[type="text"]::placeholder {
      color: rgba(10, 17, 40, 0.6);
      font-family: 'Anek Latin', sans-serif;
      font-weight: 500;
    }
    
    button.send-btn { 
      padding: 14px 22px; 
      font-weight: 700; 
      background: linear-gradient(135deg, var(--copper), var(--copper-light));
      color: var(--navy);
      border: none;
      border-radius: var(--radius);
      cursor: pointer;
      transition: transform 0.2s, box-shadow 0.3s;
      font-family: 'Poppins', sans-serif;
    }
    
    button.send-btn:hover {
      transform: translateY(-2px);
      box-shadow: 0 6px 18px rgba(255,182,127,0.5);
    }

    #response { 
      background: rgba(255,255,255,0.1); 
      border-radius: var(--radius); 
      padding: 22px; 
      min-height: 80px; 
      color: var(--copper-light); 
      font-size: 1.1em; 
      transition: all 0.3s ease; 
      text-align: left; 
      white-space: pre-line;
      font-family: 'Poppins', sans-serif;
    }
    
    footer { 
      margin-top: 30px; 
      font-size: 0.9em; 
      color: var(--gray); 
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="logo-container">
      <div class="logo-glow"></div>
      <div class="logo-base">
        <div class="logo-connections">
          <div class="connection connection-1"></div>
          <div class="connection connection-2"></div>
          <div class="connection connection-3"></div>
        </div>
        <div class="logo-brain"></div>
        <div class="logo-sparkles">
          <div class="sparkle sparkle-1"></div>
          <div class="sparkle sparkle-2"></div>
          <div class="sparkle sparkle-3"></div>
          <div class="sparkle sparkle-4"></div>
        </div>
      </div>
    </div>
    
    <h1>Gazali AI</h1>
    <p>Gazali AI — your ultra-intelligent assistant, able to answer any question with detailed, step-by-step explanations.</p>

    <div class="options">
      <button onclick="askQuestion('What is Artificial Intelligence?')">What is AI?</button>
      <button onclick="askQuestion('Explain a Malayalam poem')">Explain a poem</button>
      <button onclick="askQuestion('Solve a math problem')">Solve math</button>
      <button onclick="askQuestion('Tell me something interesting')">Something interesting</button>
      <button onclick="askQuestion('Who created Gazali AI?')">Who created Gazali AI?</button>
      <button onclick="askQuestion('Hi')">Say Hi</button>
      <button onclick="askQuestion('Hello')">Say Hello</button>
      <button onclick="askQuestion('How are you?')">How are you?</button>
      <button onclick="askQuestion('What is your name?')">Your name</button>
      <button onclick="askQuestion('What is the future of AI?')">Future of AI</button>
      <button onclick="askQuestion('Thank you')">Thank you</button>
      <button onclick="askQuestion('What time is it?')">Current time</button>
      <button onclick="askQuestion('What is the date today?')">Today's date</button>
      <button onclick="askQuestion('Help me with coding')">Coding help</button>
      <button onclick="askQuestion('JavaScript question')">JavaScript</button>
      <button onclick="askQuestion('Python question')">Python</button>
    </div>

    <div class="input-group">
      <input type="text" id="userInput" placeholder="Type your question...">
      <button class="send-btn" onclick="getAnswer()">Ask</button>
    </div>

    <div id="response">Gazali is ready to help you...</div>
    <footer>&copy; 2025 Gazali AI. All rights reserved.</footer>
  </div>

  <script>
    function askQuestion(q) {
      document.getElementById('userInput').value = q;
      getAnswer();
    }

    function getAnswer() {
      const input = document.getElementById('userInput').value.trim();
      const response = document.getElementById('response');
      let answer = "Gazali: I am extremely capable. Please provide your question!";
      const s = input.toLowerCase();

      const knowledge = {
        'hello': 'Hello! I am Gazali, ready to provide detailed answers.',
        'hi': 'Hi there! Ask me anything and I will give a full answer.',
        'how are you': 'I am fully operational and ready to assist!',
        'your name': 'I am Gazali AI — your ultimate AI assistant.',
        'what is artificial intelligence': 'AI (Artificial Intelligence) enables machines to perform tasks that require human intelligence such as reasoning, learning, and problem-solving.',
        'what is ai': 'AI allows computers to perform intelligent tasks, from solving problems to understanding language.',
        'future of ai': 'AI will transform industries, education, healthcare, and everyday life by enhancing efficiency and decision-making.',
        'thank you': 'You\'re welcome! Ask me anything else and I\'ll provide a thorough explanation.',
        'time': `Current time: ${new Date().toLocaleTimeString()}.`,
        'date': `Today is: ${new Date().toLocaleDateString()}.`,
        'malayalam poem': 'Gazali: Malayalam literature is rich and diverse. I can provide summaries or detailed explanations line-by-line.',
        'solve math problem': 'Gazali: I can solve math problems step-by-step and explain each part clearly.',
        'code': 'Gazali: I can assist with coding examples, debugging, and programming guidance.',
        'javascript': 'Gazali: Ask me JavaScript questions, and I can explain or provide code samples.',
        'python': 'Gazali: I can provide Python examples, code help, and detailed explanations.',
        'who created gazali ai': 'Hasan Gazali, he is a motion designer from Kerala.',
        'help': 'I can help with questions about AI, programming, math, literature, and more. Try asking me specific questions or use the buttons above.',
        'good morning': 'Good morning! How can I assist you today?',
        'good afternoon': 'Good afternoon! What would you like to know?',
        'good evening': 'Good evening! I\'m here to help with your questions.',
        'bye': 'Goodbye! Feel free to return if you have more questions.',
        'goodbye': 'Goodbye! Have a great day.'
      };

      // Check for exact matches first
      let matched = false;
      for (const key in knowledge) {
        if (s === key.toLowerCase()) {
          answer = knowledge[key];
          matched = true;
          break;
        }
      }
      
      // If no exact match, check for partial matches
      if (!matched) {
        for (const key in knowledge) {
          if (s.includes(key)) {
            answer = knowledge[key];
            break;
          }
        }
      }

      response.textContent = answer;
      document.getElementById('userInput').value = '';
    }

    document.getElementById('userInput').addEventListener('keypress', function(e){
      if(e.key === 'Enter') getAnswer();
    });
  </script>
</body>
</html>
