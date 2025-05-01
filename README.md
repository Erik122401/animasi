<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Langit Malam Romantis</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Arial', sans-serif;
        }
        
        body {
            height: 100vh;
            background: linear-gradient(to bottom, #0a0a2a, #1a1a4a);
            overflow: hidden;
            display: flex;
            flex-direction: column;
            justify-content: flex-end;
            position: relative;
        }
        
        .stars {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 0;
        }
        
        .star {
            position: absolute;
            background-color: white;
            border-radius: 50%;
            animation: twinkle 2s infinite ease-in-out;
        }
        
        .moon {
            position: absolute;
            top: 50px;
            right: 100px;
            width: 100px;
            height: 100px;
            background-color: #fffde7;
            border-radius: 50%;
            box-shadow: 0 0 30px 5px #fff9c4;
            animation: glow 4s infinite alternate;
        }
        
        .shooting-star {
            position: absolute;
            width: 3px;
            height: 3px;
            background: linear-gradient(to right, transparent, white, transparent);
            border-radius: 50%;
            animation: shoot 5s linear infinite;
            opacity: 0;
        }
        
        @keyframes twinkle {
            0%, 100% { opacity: 0.3; }
            50% { opacity: 1; }
        }
        
        @keyframes glow {
            0% { box-shadow: 0 0 30px 5px #fff9c4; }
            100% { box-shadow: 0 0 40px 10px #fff9c4; }
        }
        
        @keyframes shoot {
            0% {
                transform: translate(0, 0) rotate(-45deg) scale(0);
                opacity: 0;
            }
            5% {
                opacity: 1;
            }
            15% {
                transform: translate(-300px, 300px) rotate(-45deg) scale(1);
                opacity: 0;
            }
            100% {
                transform: translate(-300px, 300px) rotate(-45deg) scale(1);
                opacity: 0;
            }
        }
        
        .chat-container {
            width: 90%;
            max-width: 500px;
            height: 60%;
            max-height: 500px;
            margin: 0 auto 20px;
            background-color: rgba(0, 0, 0, 0.5);
            border-radius: 15px;
            backdrop-filter: blur(5px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            display: flex;
            flex-direction: column;
            z-index: 10;
            position: relative;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
        }
        
        .chat-header {
            padding: 15px;
            text-align: center;
            color: white;
            border-bottom: 1px solid rgba(255, 255, 255, 0.2);
        }
        
        .chat-messages {
            flex: 1;
            overflow-y: auto;
            padding: 15px;
            display: flex;
            flex-direction: column;
        }
        
        .message {
            margin-bottom: 15px;
            padding: 10px 15px;
            border-radius: 20px;
            max-width: 70%;
            word-wrap: break-word;
            animation: fadeIn 0.3s ease-in-out;
        }
        
        .received {
            align-self: flex-start;
            background-color: rgba(75, 75, 150, 0.7);
            color: white;
            border-bottom-left-radius: 5px;
        }
        
        .sent {
            align-self: flex-end;
            background-color: rgba(100, 100, 200, 0.7);
            color: white;
            border-bottom-right-radius: 5px;
        }
        
        .chat-input {
            display: flex;
            padding: 15px;
            border-top: 1px solid rgba(255, 255, 255, 0.2);
        }
        
        .message-input {
            flex: 1;
            padding: 10px 15px;
            border-radius: 20px;
            border: none;
            background-color: rgba(255, 255, 255, 0.1);
            color: white;
            margin-right: 10px;
        }
        
        .message-input::placeholder {
            color: rgba(255, 255, 255, 0.5);
        }
        
        .send-button {
            padding: 10px 20px;
            border-radius: 20px;
            border: none;
            background-color: #7e57c2;
            color: white;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        
        .send-button:hover {
            background-color: #9575cd;
        }
        
        .floating-hearts {
            position: absolute;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 5;
        }
        
        .heart {
            position: absolute;
            font-size: 20px;
            color: #ff4081;
            animation: float 10s linear infinite;
            opacity: 0;
        }
        
        @keyframes float {
            0% {
                transform: translateY(100vh) scale(0.5);
                opacity: 0;
            }
            10% {
                opacity: 1;
            }
            90% {
                opacity: 1;
            }
            100% {
                transform: translateY(-50px) scale(1.5);
                opacity: 0;
            }
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        /* Custom scrollbar */
        .chat-messages::-webkit-scrollbar {
            width: 5px;
        }
        
        .chat-messages::-webkit-scrollbar-track {
            background: rgba(0, 0, 0, 0.2);
        }
        
        .chat-messages::-webkit-scrollbar-thumb {
            background: rgba(255, 255, 255, 0.3);
            border-radius: 10px;
        }
        
        /* Custom textarea */
        .message-input:focus {
            outline: none;
            background-color: rgba(255, 255, 255, 0.2);
        }
        
        /* Mobile responsiveness */
        @media (max-width: 600px) {
            .chat-container {
                width: 95%;
                height: 70%;
            }
            
            .moon {
                width: 70px;
                height: 70px;
                top: 30px;
                right: 30px;
            }
        }
    </style>
</head>
<body>
    <div class="stars"></div>
    <div class="moon"></div>
    <div class="floating-hearts"></div>
    
    <div class="chat-container">
        <div class="chat-header">
            <h2>BUATMU FAJRIYAH</h2>
        </div>
        <div class="chat-messages" id="chatMessages">
            <div class="message received">
                Halo, apa kabar? Indah sekali langit malam ini...
            </div>
        </div>
        <div class="chat-input">
            <input type="text" class="message-input" id="messageInput" placeholder="Tulis pesan romantismu...">
            <button class="send-button" id="sendButton">Kirim</button>
        </div>
    </div>
    
    <script>
        // Create stars
        function createStars() {
            const starsContainer = document.querySelector('.stars');
            const starsCount = 200;
            
            for (let i = 0; i < starsCount; i++) {
                const star = document.createElement('div');
                star.classList.add('star');
                
                // Random position
                const posX = Math.random() * 100;
                const posY = Math.random() * 100;
                
                // Random size
                const size = Math.random() * 3;
                
                // Random animation delay
                const delay = Math.random() * 5;
                
                star.style.left = `${posX}%`;
                star.style.top = `${posY}%`;
                star.style.width = `${size}px`;
                star.style.height = `${size}px`;
                star.style.animationDelay = `${delay}s`;
                
                starsContainer.appendChild(star);
            }
        }
        
        // Create shooting stars
        function createShootingStars() {
            const starsContainer = document.querySelector('.stars');
            const shootingStarsCount = 5;
            
            for (let i = 0; i < shootingStarsCount; i++) {
                const shootingStar = document.createElement('div');
                shootingStar.classList.add('shooting-star');
                
                // Random position
                const posX = Math.random() * 100;
                const posY = Math.random() * 30;
                
                // Random animation delay
                const delay = Math.random() * 15;
                
                shootingStar.style.left = `${posX}%`;
                shootingStar.style.top = `${posY}%`;
                shootingStar.style.animationDelay = `${delay}s`;
                
                starsContainer.appendChild(shootingStar);
            }
        }
        
        // Create floating hearts
        function createFloatingHearts() {
            const heartsContainer = document.querySelector('.floating-hearts');
            const heartsCount = 20;
            
            for (let i = 0; i < heartsCount; i++) {
                const heart = document.createElement('div');
                heart.classList.add('heart');
                heart.innerHTML = '❤️';
                
                // Random position
                const posX = Math.random() * 100;
                
                // Random animation delay
                const delay = Math.random() * 30;
                
                heart.style.left = `${posX}%`;
                heart.style.animationDelay = `${delay}s`;
                
                heartsContainer.appendChild(heart);
            }
        }
        
        // Handle chat functionality
        function initChat() {
            const messageInput = document.getElementById('messageInput');
            const sendButton = document.getElementById('sendButton');
            const chatMessages = document.getElementById('chatMessages');
            
            // Predefined romantic responses
            const romanticResponses = [
                "Seperti bintang di langit, matamu selalu bersinar indah...",
                "Cintaku padamu seperti langit malam ini, tak terbatas dan penuh keajaiban.",
                "Jika aku bisa meminta satu bintang jatuh, aku akan meminta bersamamu selamanya hehe.",
                "Di bawah langit malam ini, aku berjanji untuk selalu mencintaimu.",
                "Cinta kita seperti bulan yang selalu menyinari malam tergelap sekalipun.",
                "Saat bersamamu, aku merasa seperti melayang di antara bintang-bintang.",
                "Kamu adalah bintang paling terang dalam hidupku.",
                "Seindah malam ini, tapi masih tak seindah senyumanmu.",
                "Bahkan bulan cemburu melihat betapa bersinarnya dirimu malam ini.",
                "Bintang-bintang menjadi saksi cinta kita yang abadi."
            ];
            
            function addMessage(text, isSent) {
                const message = document.createElement('div');
                message.classList.add('message');
                message.classList.add(isSent ? 'sent' : 'received');
                message.textContent = text;
                
                chatMessages.appendChild(message);
                chatMessages.scrollTop = chatMessages.scrollHeight;
                
                // Create hearts when sending a loving message
                if (isSent) {
                    setTimeout(() => {
                        addResponse();
                    }, 1000);
                }
            }
            
            function addResponse() {
                const randomIndex = Math.floor(Math.random() * romanticResponses.length);
                addMessage(romanticResponses[randomIndex], false);
            }
            
            function sendMessage() {
                const text = messageInput.value.trim();
                if (text) {
                    addMessage(text, true);
                    messageInput.value = '';
                }
            }
            
            sendButton.addEventListener('click', sendMessage);
            messageInput.addEventListener('keypress', (e) => {
                if (e.key === 'Enter') {
                    sendMessage();
                }
            });
            
            // Local storage for chat persistence
            function saveChat() {
                const messages = [];
                document.querySelectorAll('.message').forEach(msg => {
                    messages.push({
                        text: msg.textContent,
                        isSent: msg.classList.contains('sent')
                    });
                });
                
                localStorage.setItem('romanticChatMessages', JSON.stringify(messages));
            }
            
            function loadChat() {
                const saved = localStorage.getItem('romanticChatMessages');
                if (saved) {
                    chatMessages.innerHTML = '';
                    const messages = JSON.parse(saved);
                    messages.forEach(msg => {
                        addMessage(msg.text, msg.isSent);
                    });
                }
            }
            
            // Save chat when window is closed
            window.addEventListener('beforeunload', saveChat);
            
            // Try to load saved chat
            loadChat();
        }
        
        // Initialize
        document.addEventListener('DOMContentLoaded', () => {
            createStars();
            createShootingStars();
            createFloatingHearts();
            initChat();
        });
    </script>
</body>
</html>
