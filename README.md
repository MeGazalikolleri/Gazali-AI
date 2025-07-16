<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gazali AI - Your Intelligent Assistant</title>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary-blue: #007bff; /* A vibrant blue for accents */
            --dark-blue: #0056b3;   /* A darker blue for hover states */
            --light-gray: #f8f9fa;  /* Very light gray for background */
            --medium-gray: #e9ecef; /* Slightly darker gray for containers */
            --dark-gray: #343a40;   /* Dark charcoal for text */
            --white: #ffffff;
            --border-radius: 8px;
            --box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
        }

        body {
            font-family: 'Roboto', sans-serif;
            margin: 0;
            padding: 0;
            background-color: var(--light-gray);
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            color: var(--dark-gray);
            line-height: 1.6;
        }

        .container {
            background-color: var(--white);
            border-radius: var(--border-radius);
            box-shadow: var(--box-shadow);
            width: 90%;
            max-width: 700px;
            padding: 30px;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .container::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 10px;
            background: linear-gradient(to right, var(--primary-blue), var(--dark-blue));
            border-top-left-radius: var(--border-radius);
            border-top-right-radius: var(--border-radius);
        }

        h1 {
            color: var(--primary-blue);
            margin-bottom: 20px;
            font-weight: 700;
            font-size: 2.5em;
        }

        .gazali-logo {
            width: 80px;
            height: 80px;
            background-color: var(--primary-blue);
            border-radius: 50%;
            margin: 0 auto 25px;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 2.5em;
            color: var(--white);
            font-weight: 700;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.15);
        }

        p {
            margin-bottom: 25px;
            font-size: 1.1em;
            color: #555;
        }

        .input-group {
            display: flex;
            margin-bottom: 25px;
            gap: 10px;
        }

        input[type="text"] {
            flex-grow: 1;
            padding: 15px;
            border: 1px solid var(--medium-gray);
            border-radius: var(--border-radius);
            font-size: 1em;
            outline: none;
            transition: border-color 0.3s ease;
        }

        input[type="text"]:focus {
            border-color: var(--primary-blue);
        }

        button {
            padding: 15px 25px;
            background-color: var(--primary-blue);
            color: var(--white);
            border: none;
            border-radius: var(--border-radius);
            font-size: 1em;
            cursor: pointer;
            transition: background-color 0.3s ease, transform 0.2s ease;
            font-weight: 600;
            letter-spacing: 0.5px;
        }

        button:hover {
            background-color: var(--dark-blue);
            transform: translateY(-2px);
        }

        #gazali-response {
            background-color: var(--medium-gray);
            border-radius: var(--border-radius);
            padding: 20px;
            min-height: 60px;
            text-align: left;
            word-wrap: break-word;
            line-height: 1.8;
            color: var(--dark-gray);
            font-size: 1.05em;
            box-shadow: inset 0 1px 3px rgba(0, 0, 0, 0.08);
            display: flex;
            align-items: center;
            justify-content: center;
            font-style: italic;
        }

        #gazali-response.active {
            animation: fadeIn 0.5s ease-in-out;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        footer {
            margin-top: 30px;
            font-size: 0.9em;
            color: #777;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="gazali-logo">G</div>
        <h1>Meet Gazali</h1>
        <p>Your intelligent assistant, ready to answer your questions.</p>

        <div class="input-group">
            <input type="text" id="user-input" placeholder="Ask Gazali anything...">
            <button onclick="getGazaliAnswer()">Ask</button>
        </div>

        <div id="gazali-response">
            Gazali's response will appear here...
        </div>

        <footer>
            &copy; 2025 Gazali AI. All rights reserved.
        </footer>
    </div>

    <script>
        function getGazaliAnswer() {
            const userInput = document.getElementById('user-input').value.trim().toLowerCase();
            const responseDiv = document.getElementById('gazali-response');
            let answer = "I'm still learning, please try asking something different!";

            if (userInput.includes("hello") || userInput.includes("hi")) {
                answer = "Hello there! How can I assist you today?";
            } else if (userInput.includes("how are you")) {
                answer = "I am a program, so I don't have feelings, but I'm ready to help!";
            } else if (userInput.includes("what is your name")) {
                answer = "My name is Gazali, your intelligent assistant.";
            } else if (userInput.includes("weather")) {
                answer = "I don't have real-time weather data. Perhaps you could check a weather app?";
            } else if (userInput.includes("time")) {
                const now = new Date();
                answer = `The current time is ${now.toLocaleTimeString()}.`;
            } else if (userInput.includes("date")) {
                const now = new Date();
                answer = `Today's date is ${now.toLocaleDateString()}.`;
            } else if (userInput.includes("thank you")) {
                answer = "You're most welcome! Is there anything else I can do?";
            } else if (userInput.includes("capabilities") || userInput.includes("can you do")) {
                answer = "I can answer questions based on my programming, provide information, and engage in basic conversation. What would you like to know?";
            } else if (userInput === "") {
                answer = "Please type a question for Gazali!";
            } else if (userInput.includes("what is ai")) {
                answer = "AI, or Artificial Intelligence, is a broad field of computer science that enables machines to perform tasks that typically require human intelligence.";
            } else if (userInput.includes("history of ai")) {
                answer = "The concept of AI dates back to ancient times, but modern AI began with the development of programmable computers. The term 'artificial intelligence' was coined in 1956.";
            } else if (userInput.includes("future of ai")) {
                answer = "The future of AI holds immense potential, from advanced automation to personalized medicine and more sophisticated human-computer interactions.";
            }

            responseDiv.textContent = answer;
            responseDiv.classList.add('active'); // Add class for animation
            setTimeout(() => responseDiv.classList.remove('active'), 600); // Remove after animation
            document.getElementById('user-input').value = ''; // Clear input
        }

        // Allow pressing Enter to submit
        document.getElementById('user-input').addEventListener('keypress', function(event) {
            if (event.key === 'Enter') {
                getGazaliAnswer();
            }
        });
    </script>
</body>
</html>
