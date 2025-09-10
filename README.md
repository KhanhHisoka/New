<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🧊 Trò Chơi Ma Thuật Tri Thức - Rem Style</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@300;400;700;900&family=Cute+Font&display=swap');
        
        * {
            font-family: 'Noto Sans JP', sans-serif;
        }
        
        .kawaii-font {
            font-family: 'Cute Font', cursive;
        }
        
        body {
            background: transparent;
            position: relative;
            overflow-x: hidden;
        }
        
        @keyframes dreamyFlow {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }
        
        /* Snowfall Effect */
        .snowflake {
            position: fixed;
            top: -10px;
            color: rgba(255, 255, 255, 0.8);
            font-size: 1em;
            animation: snowfall linear infinite;
            pointer-events: none;
            z-index: 1;
        }
        
        @keyframes snowfall {
            0% { transform: translateY(-100vh) rotate(0deg); }
            100% { transform: translateY(100vh) rotate(360deg); }
        }
        
        /* Ice Magic Particles */
        .ice-particle {
            position: fixed;
            width: 4px;
            height: 4px;
            background: radial-gradient(circle, #60a5fa, #3b82f6);
            border-radius: 50%;
            animation: iceFloat 4s linear infinite;
            pointer-events: none;
            z-index: 1;
        }
        
        @keyframes iceFloat {
            0% { 
                transform: translateY(100vh) translateX(0) scale(0);
                opacity: 0;
            }
            10% {
                opacity: 1;
            }
            90% {
                opacity: 1;
            }
            100% { 
                transform: translateY(-10vh) translateX(50px) scale(1);
                opacity: 0;
            }
        }
        
        /* Crystal Ball Effects */
        @keyframes crystalFloat {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            33% { transform: translateY(-8px) rotate(2deg); }
            66% { transform: translateY(4px) rotate(-1deg); }
        }
        
        @keyframes crystalGlow {
            0%, 100% { 
                box-shadow: 0 0 20px rgba(96, 165, 250, 0.6), 
                           0 0 40px rgba(59, 130, 246, 0.4),
                           inset 0 0 20px rgba(255, 255, 255, 0.2);
            }
            50% { 
                box-shadow: 0 0 30px rgba(96, 165, 250, 0.8), 
                           0 0 60px rgba(59, 130, 246, 0.6),
                           inset 0 0 30px rgba(255, 255, 255, 0.3);
            }
        }
        
        @keyframes iceBounce {
            0%, 20%, 50%, 80%, 100% { transform: translateY(0) scale(1); }
            40% { transform: translateY(-12px) scale(1.05); }
            60% { transform: translateY(-6px) scale(1.02); }
        }
        
        @keyframes frostShimmer {
            0%, 100% { background-position: -200% 0; }
            100% { background-position: 200% 0; }
        }
        
        .crystal-ball {
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            cursor: pointer;
            position: relative;
            border: 2px solid rgba(255, 255, 255, 0.3);
            backdrop-filter: blur(15px);
            animation: crystalFloat 8s ease-in-out infinite;
            background: linear-gradient(135deg, 
                rgba(255, 255, 255, 0.2), 
                rgba(96, 165, 250, 0.3), 
                rgba(59, 130, 246, 0.2));
        }
        
        .crystal-ball::before {
            content: '';
            position: absolute;
            top: -2px;
            left: -2px;
            right: -2px;
            bottom: -2px;
            background: linear-gradient(45deg, 
                transparent, 
                rgba(255, 255, 255, 0.5), 
                transparent,
                rgba(96, 165, 250, 0.5),
                transparent);
            background-size: 400% 400%;
            border-radius: 50%;
            z-index: -1;
            opacity: 0;
            transition: opacity 0.3s ease;
            animation: frostShimmer 3s linear infinite;
        }
        
        .crystal-ball:hover {
            animation: iceBounce 0.8s ease-in-out;
            transform: scale(1.1);
            box-shadow: 0 15px 35px rgba(59, 130, 246, 0.4);
        }
        
        .crystal-ball:hover::before {
            opacity: 1;
        }
        
        .crystal-ball.completed {
            animation: crystalGlow 2s infinite, crystalFloat 8s ease-in-out infinite;
            border-color: rgba(96, 165, 250, 0.8);
        }
        
        /* Ice Magic Click Effect */
        @keyframes iceBlast {
            0% { transform: scale(1); opacity: 1; }
            50% { transform: scale(1.2); opacity: 0.8; }
            100% { transform: scale(0.8); opacity: 0; }
        }
        
        .ice-blast {
            animation: iceBlast 0.5s ease-out;
        }
        
        /* Kawaii Modal Styling */
        .kawaii-modal {
            backdrop-filter: blur(25px);
            background: rgba(30, 58, 138, 0.8);
        }
        
        .kawaii-content {
            background: linear-gradient(135deg, 
                rgba(255, 255, 255, 0.95), 
                rgba(240, 249, 255, 0.9),
                rgba(219, 234, 254, 0.95));
            backdrop-filter: blur(20px);
            border: 2px solid rgba(96, 165, 250, 0.3);
            box-shadow: 0 25px 50px rgba(59, 130, 246, 0.3);
        }
        
        /* Anime Button Styling */
        .anime-btn {
            transition: all 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            background: linear-gradient(135deg, 
                rgba(219, 234, 254, 0.8), 
                rgba(191, 219, 254, 0.6));
            border: 2px solid rgba(96, 165, 250, 0.4);
            backdrop-filter: blur(10px);
            position: relative;
            overflow: hidden;
        }
        
        .anime-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, 
                transparent, 
                rgba(255, 255, 255, 0.6), 
                transparent);
            transition: left 0.6s ease;
        }
        
        .anime-btn:hover {
            transform: translateY(-2px) scale(1.02);
            box-shadow: 0 10px 25px rgba(96, 165, 250, 0.4);
            border-color: rgba(96, 165, 250, 0.7);
            background: linear-gradient(135deg, 
                rgba(219, 234, 254, 1), 
                rgba(191, 219, 254, 0.8));
        }
        
        .anime-btn:hover::before {
            left: 100%;
        }
        
        /* Magic Effects */
        .correct-magic {
            background: linear-gradient(135deg, #10b981, #059669);
            animation: correctPulse 1.2s ease-out;
            color: white;
            border-color: #10b981;
        }
        
        .incorrect-magic {
            background: linear-gradient(135deg, #f472b6, #ec4899);
            animation: incorrectShake 0.6s ease-out;
            color: white;
            border-color: #f472b6;
        }
        
        @keyframes correctPulse {
            0% { transform: scale(1); box-shadow: 0 0 0 0 rgba(16, 185, 129, 0.7); }
            70% { transform: scale(1.05); box-shadow: 0 0 0 15px rgba(16, 185, 129, 0); }
            100% { transform: scale(1); box-shadow: 0 0 0 0 rgba(16, 185, 129, 0); }
        }
        
        @keyframes incorrectShake {
            0%, 100% { transform: translateX(0) rotate(0deg); }
            10%, 30%, 50%, 70%, 90% { transform: translateX(-8px) rotate(-2deg); }
            20%, 40%, 60%, 80% { transform: translateX(8px) rotate(2deg); }
        }
        
        /* Magical Progress Bar */
        .magic-progress {
            background: rgba(255, 255, 255, 0.2);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(96, 165, 250, 0.3);
        }
        
        .progress-magic {
            background: linear-gradient(90deg, #10b981, #3b82f6, #8b5cf6, #ec4899);
            box-shadow: 0 0 20px rgba(59, 130, 246, 0.6);
            animation: progressGlow 2s ease-in-out infinite;
        }
        
        @keyframes progressGlow {
            0%, 100% { box-shadow: 0 0 20px rgba(59, 130, 246, 0.6); }
            50% { box-shadow: 0 0 30px rgba(59, 130, 246, 0.8); }
        }
        
        /* Kawaii Score Display */
        .kawaii-score {
            background: linear-gradient(135deg, 
                rgba(255, 255, 255, 0.3), 
                rgba(219, 234, 254, 0.4));
            backdrop-filter: blur(15px);
            border: 2px solid rgba(96, 165, 250, 0.4);
            border-radius: 25px;
            padding: 12px 24px;
            display: inline-block;
            box-shadow: 0 8px 25px rgba(59, 130, 246, 0.2);
        }
        
        /* Title Magic Glow */
        .magic-title {
            animation: titleMagic 4s ease-in-out infinite;
            text-shadow: 0 0 20px rgba(96, 165, 250, 0.8);
        }
        
        @keyframes titleMagic {
            0%, 100% { 
                text-shadow: 0 0 20px rgba(251, 146, 60, 0.8), 
                           0 0 40px rgba(249, 115, 22, 0.6); 
            }
            50% { 
                text-shadow: 0 0 30px rgba(251, 146, 60, 1), 
                           0 0 60px rgba(249, 115, 22, 0.8); 
            }
        }
        
        /* Fireworks Effect */
        .magic-fireworks {
            position: relative;
        }
        
        .magic-fireworks::before {
            content: '❄️✨💎🔮💙';
            position: absolute;
            top: -30px;
            left: 50%;
            transform: translateX(-50%);
            font-size: 2.5rem;
            animation: fireworksMagic 1.5s ease-out;
            pointer-events: none;
            z-index: 1000;
        }
        
        @keyframes fireworksMagic {
            0% { transform: translateX(-50%) scale(0) rotate(0deg); opacity: 1; }
            50% { transform: translateX(-50%) scale(1.5) rotate(180deg); opacity: 0.8; }
            100% { transform: translateX(-50%) scale(0) rotate(360deg); opacity: 0; }
        }
        
        /* Reward System Animations */
        @keyframes fadeIn {
            from { opacity: 0; transform: scale(0.8); }
            to { opacity: 1; transform: scale(1); }
        }
        
        @keyframes fadeOut {
            from { opacity: 1; transform: scale(1); }
            to { opacity: 0; transform: scale(0.8); }
        }
        
        @keyframes titleGlow {
            0%, 100% { 
                text-shadow: 0 0 20px rgba(251, 191, 36, 0.8), 0 0 40px rgba(249, 115, 22, 0.6); 
            }
            50% { 
                text-shadow: 0 0 30px rgba(251, 191, 36, 1), 0 0 60px rgba(249, 115, 22, 0.8); 
            }
        }
        
        @keyframes shimmer {
            0% { transform: translateX(-100%) translateY(-100%) rotate(45deg); }
            100% { transform: translateX(100%) translateY(100%) rotate(45deg); }
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
        }
        
        @keyframes pointerGlow {
            0%, 100% { 
                box-shadow: 0 0 20px #ef4444, inset 0 0 10px rgba(255,255,255,0.3); 
            }
            50% { 
                box-shadow: 0 0 30px #ef4444, 0 0 40px #ef4444, inset 0 0 15px rgba(255,255,255,0.5); 
            }
        }
        
        @keyframes bounceIn {
            0% { transform: scale(0.3) translateY(50px); opacity: 0; }
            50% { transform: scale(1.05) translateY(-10px); opacity: 0.8; }
            70% { transform: scale(0.9) translateY(0px); opacity: 0.9; }
            100% { transform: scale(1) translateY(0px); opacity: 1; }
        }
        
        @keyframes fireworkExplode {
            0% { 
                transform: scale(0) rotate(0deg); 
                opacity: 1; 
            }
            50% { 
                transform: scale(1.5) rotate(180deg); 
                opacity: 0.8; 
            }
            100% { 
                transform: scale(0) rotate(360deg) translateY(-100px); 
                opacity: 0; 
            }
        }
        
        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.6; }
        }
    </style>
</head>
<body class="min-h-screen text-white">
    <!-- Snowfall Effect -->
    <div id="snowfall"></div>
    
    <!-- Ice Particles -->
    <div id="iceParticles"></div>
    
    <div class="container mx-auto px-4 py-8 relative z-10">
        <!-- Kawaii Header -->
        <div class="text-center mb-12 relative">
            <h1 class="kawaii-font text-6xl font-black mb-6 bg-gradient-to-r from-orange-300 via-yellow-200 to-pink-300 bg-clip-text text-transparent magic-title" style="font-weight: 900; -webkit-text-stroke: 1px rgba(251, 146, 60, 0.4);">
                ❄️ Ma Thuật Tri Thức Rem ❄️
            </h1>
            <div class="relative inline-block">
                <p class="text-3xl font-black text-orange-200 mb-6 drop-shadow-lg" style="font-weight: 900; -webkit-text-stroke: 0.5px rgba(251, 146, 60, 0.3); text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);">
                    🔮 Chạm vào các quả cầu ma thuật để trả lời câu hỏi! 🔮
                </p>
            </div>
            <div class="kawaii-score mt-6">
                <span class="text-xl font-black text-blue-800" style="font-weight: 900;">💎 Điểm Ma Thuật: </span>
                <span id="score" class="text-3xl font-black text-blue-600" style="font-weight: 900;">0/7</span>
            </div>
        </div>

        <!-- Magic Crystal Balls -->
        <div class="flex flex-col items-center justify-center min-h-[400px] mb-8 space-y-8">
            <!-- Top Row - 4 Crystal Balls -->
            <div class="flex justify-center items-center gap-8">
                <!-- Crystal Ball 1 -->
                <div class="crystal-ball w-32 h-32 bg-gradient-to-br from-blue-400 to-blue-600 rounded-full flex items-center justify-center text-2xl font-bold shadow-lg" 
                     onclick="openQuestion(0)">
                    <span>❄️</span>
                </div>
                
                <!-- Crystal Ball 2 -->
                <div class="crystal-ball w-32 h-32 bg-gradient-to-br from-indigo-400 to-indigo-600 rounded-full flex items-center justify-center text-2xl font-bold shadow-lg" 
                     onclick="openQuestion(1)">
                    <span>🔮</span>
                </div>
                
                <!-- Crystal Ball 3 -->
                <div class="crystal-ball w-32 h-32 bg-gradient-to-br from-cyan-400 to-cyan-600 rounded-full flex items-center justify-center text-2xl font-bold shadow-lg" 
                     onclick="openQuestion(2)">
                    <span>💎</span>
                </div>
                
                <!-- Crystal Ball 4 -->
                <div class="crystal-ball w-32 h-32 bg-gradient-to-br from-sky-400 to-sky-600 rounded-full flex items-center justify-center text-2xl font-bold shadow-lg" 
                     onclick="openQuestion(3)">
                    <span>🌟</span>
                </div>
            </div>
            
            <!-- Bottom Row - 3 Crystal Balls -->
            <div class="flex justify-center items-center gap-8">
                <!-- Crystal Ball 5 -->
                <div class="crystal-ball w-32 h-32 bg-gradient-to-br from-blue-500 to-purple-500 rounded-full flex items-center justify-center text-2xl font-bold shadow-lg" 
                     onclick="openQuestion(4)">
                    <span>✨</span>
                </div>
                
                <!-- Crystal Ball 6 -->
                <div class="crystal-ball w-32 h-32 bg-gradient-to-br from-indigo-500 to-purple-600 rounded-full flex items-center justify-center text-2xl font-bold shadow-lg" 
                     onclick="openQuestion(5)">
                    <span>🌙</span>
                </div>
                
                <!-- Crystal Ball 7 -->
                <div class="crystal-ball w-32 h-32 bg-gradient-to-br from-purple-500 to-pink-500 rounded-full flex items-center justify-center text-2xl font-bold shadow-lg" 
                     onclick="openQuestion(6)">
                    <span>💫</span>
                </div>
            </div>
        </div>

        <!-- Magic Progress Bar -->
        <div class="flex flex-col items-center justify-center max-w-lg mx-auto mb-8">
            <div class="text-center mb-3">
                <span class="text-lg font-black text-blue-100" style="font-weight: 900;">🚀 Ma Thuật Tiến Độ</span>
            </div>
            <div class="magic-progress rounded-full h-6 p-1 w-full">
                <div id="progress" class="progress-magic h-4 rounded-full transition-all duration-700 ease-out" style="width: 0%"></div>
            </div>
        </div>
    </div>

    <!-- Kawaii Question Modal -->
    <div id="questionModal" class="fixed inset-0 kawaii-modal hidden flex items-center justify-center z-50 p-4">
        <div class="kawaii-content text-gray-800 rounded-3xl p-8 max-w-2xl w-full mx-auto relative flex flex-col items-center">
            <div class="absolute top-4 right-4">
                <span class="text-3xl">🤔</span>
            </div>
            <div class="text-center mb-8 w-full">
                <h2 class="kawaii-font text-3xl font-black mb-4 text-blue-600" style="font-weight: 900;">
                    ❓ Câu Hỏi Ma Thuật <span id="questionNumber"></span>
                </h2>
                <p id="questionText" class="text-xl font-bold leading-relaxed text-gray-700" style="font-weight: 700;"></p>
            </div>
            
            <div class="space-y-4 w-full">
                <button class="anime-btn w-full p-5 text-left rounded-xl font-bold text-lg" onclick="selectAnswer(0)" style="font-weight: 700;">
                    <span class="font-black text-blue-600" style="font-weight: 900;">A.</span> <span id="answerA"></span>
                </button>
                <button class="anime-btn w-full p-5 text-left rounded-xl font-bold text-lg" onclick="selectAnswer(1)" style="font-weight: 700;">
                    <span class="font-black text-blue-600" style="font-weight: 900;">B.</span> <span id="answerB"></span>
                </button>
                <button class="anime-btn w-full p-5 text-left rounded-xl font-bold text-lg" onclick="selectAnswer(2)" style="font-weight: 700;">
                    <span class="font-black text-blue-600" style="font-weight: 900;">C.</span> <span id="answerC"></span>
                </button>
                <button class="anime-btn w-full p-5 text-left rounded-xl font-bold text-lg" onclick="selectAnswer(3)" style="font-weight: 700;">
                    <span class="font-black text-blue-600" style="font-weight: 900;">D.</span> <span id="answerD"></span>
                </button>
            </div>
            
            <div class="mt-8 text-center">
                <button onclick="closeModal()" class="px-8 py-3 bg-gradient-to-r from-pink-400 to-pink-500 text-white rounded-xl hover:from-pink-500 hover:to-pink-600 transition-all duration-300 font-semibold">
                    ❌ Đóng
                </button>
            </div>
        </div>
    </div>

    <!-- Kawaii Result Modal -->
    <div id="resultModal" class="fixed inset-0 kawaii-modal hidden flex items-center justify-center z-50 p-4">
        <div class="kawaii-content text-gray-800 rounded-3xl p-10 max-w-md w-full mx-auto text-center relative flex flex-col items-center justify-center">
            <div id="resultIcon" class="text-8xl mb-6"></div>
            <h3 id="resultTitle" class="kawaii-font text-3xl font-black mb-4" style="font-weight: 900;"></h3>
            <p id="resultMessage" class="text-xl mb-8 font-bold" style="font-weight: 700;"></p>
            <button onclick="closeResultModal()" class="px-8 py-4 bg-gradient-to-r from-blue-500 to-purple-600 text-white rounded-xl hover:from-blue-600 hover:to-purple-700 transition-all duration-300 font-bold text-lg shadow-lg">
                ✨ Tiếp Tục Ma Thuật
            </button>
        </div>
    </div>

    <script>
        const questions = [
            {
                question: "Lực Hấp dẫn tồn tại giữa:",
                answers: ["Trái Đất và quả táo", "Mặt Trăng và Trái Đất", "Hai học sinh trong lớp", "Tất cả trường hợp trên"],
                correct: 3
            },
            {
                question: "Trọng lực là gì?",
                answers: ["Lực ép của vật lên mặt đất", "Lực hút Trái Đất tác dụng lên vật", "Lực hút giữa Trái Đất và Mặt Trăng", "Lực hút của mọi vật tác dụng lên Trái Đất"],
                correct: 1
            },
            {
                question: "Nếu khối lượng một vật tăng gấp đôi thì lực hấp dẫn giữa nó và Trái Đất",
                answers: ["Không đổi", "Tăng 2 lần", "Giảm 2 lần", "Tăng 4 lần"],
                correct: 1
            },
            {
                question: "Nếu khoảng cách giữa hai vật tăng gấp 3, thì lực hấp dẫn:",
                answers: ["Giảm 3 lần", "Không giảm", "Giảm 6 lần", "Giảm 9 lần"],
                correct: 3
            },
            {
                question: "Định luật vạn vật hấp dẫn giúp ta:",
                answers: ["Giải thích quỹ đạo hành tinh", "Phóng vệ tinh nhân tạo", "Hiểu hiện tượng thủy triều", "Tất cả đều đúng"],
                correct: 3
            },
            {
                question: "Đại lượng nào sau đây không ảnh hưởng đến lực hấp dẫn giữa hai vật?",
                answers: ["Khối lượng vật thứ nhất", "Khối lượng vật thứ hai", "Khoảng cách giữa hai vật", "Vận tốc chuyển động của hai vật"],
                correct: 3
            },
            {
                question: "Một vật có khối lượng m đặt trên mặt đất chịu tác dụng lực hút của Trái Đất là F, nếu đưa vật đó lên độ cao bằng đúng bán kính R thì lực hấp dẫn sẽ bằng bao nhiêu?",
                answers: ["F", "1/2F", "1/3F", "1/4F"],
                correct: 3
            }
        ];

        let currentQuestion = 0;
        let score = 0;
        let answeredQuestions = new Set();

        // Create snowfall effect
        function createSnowfall() {
            const snowfall = document.getElementById('snowfall');
            const snowflakes = ['❄️', '❅', '❆', '🌨️'];
            
            for (let i = 0; i < 50; i++) {
                const snowflake = document.createElement('div');
                snowflake.className = 'snowflake';
                snowflake.innerHTML = snowflakes[Math.floor(Math.random() * snowflakes.length)];
                snowflake.style.left = Math.random() * 100 + '%';
                snowflake.style.animationDuration = (Math.random() * 3 + 2) + 's';
                snowflake.style.animationDelay = Math.random() * 2 + 's';
                snowfall.appendChild(snowflake);
            }
        }

        // Create ice particles
        function createIceParticles() {
            const container = document.getElementById('iceParticles');
            
            for (let i = 0; i < 30; i++) {
                const particle = document.createElement('div');
                particle.className = 'ice-particle';
                particle.style.left = Math.random() * 100 + '%';
                particle.style.animationDuration = (Math.random() * 2 + 3) + 's';
                particle.style.animationDelay = Math.random() * 4 + 's';
                container.appendChild(particle);
            }
        }

        function openQuestion(questionIndex) {
            if (answeredQuestions.has(questionIndex)) {
                return;
            }
            
            // Add ice blast effect
            const balls = document.querySelectorAll('.crystal-ball');
            balls[questionIndex].classList.add('ice-blast');
            setTimeout(() => {
                balls[questionIndex].classList.remove('ice-blast');
            }, 500);
            
            currentQuestion = questionIndex;
            const q = questions[questionIndex];
            
            document.getElementById('questionNumber').textContent = questionIndex + 1;
            document.getElementById('questionText').textContent = q.question;
            document.getElementById('answerA').textContent = q.answers[0];
            document.getElementById('answerB').textContent = q.answers[1];
            document.getElementById('answerC').textContent = q.answers[2];
            document.getElementById('answerD').textContent = q.answers[3];
            
            // Reset answer buttons
            const buttons = document.querySelectorAll('.anime-btn');
            buttons.forEach(btn => {
                btn.className = 'anime-btn w-full p-5 text-left rounded-xl font-medium text-lg';
                btn.disabled = false;
            });
            
            document.getElementById('questionModal').classList.remove('hidden');
        }

        function selectAnswer(answerIndex) {
            const q = questions[currentQuestion];
            const buttons = document.querySelectorAll('.anime-btn');
            
            buttons.forEach(btn => btn.disabled = true);
            
            buttons[q.correct].classList.add('correct-magic');
            
            let isCorrect = false;
            if (answerIndex === q.correct) {
                isCorrect = true;
                score++;
                document.querySelector('.kawaii-content').classList.add('magic-fireworks');
                setTimeout(() => {
                    document.querySelector('.kawaii-content').classList.remove('magic-fireworks');
                }, 1500);
            } else {
                buttons[answerIndex].classList.add('incorrect-magic');
            }
            
            answeredQuestions.add(currentQuestion);
            
            const balls = document.querySelectorAll('.crystal-ball');
            balls[currentQuestion].classList.add('completed');
            
            updateScore();
            updateProgress();
            
            setTimeout(() => {
                showResult(isCorrect);
            }, 1500);
        }

        // 🎁 Hiệu ứng mở hộp quà cải tiến với hệ thống độ hiếm
        function showReward(questionIdx) {
            const overlay = document.createElement("div");
            overlay.style.cssText = `
                position: fixed;
                top: 0;
                left: 0;
                width: 100%;
                height: 100%;
                background: linear-gradient(135deg, rgba(0,0,0,0.95), rgba(30,58,138,0.9));
                backdrop-filter: blur(10px);
                display: flex;
                flex-direction: column;
                align-items: center;
                justify-content: center;
                z-index: 9999;
                animation: fadeIn 0.5s ease-out;
            `;

            // Tiêu đề hộp quà
            const title = document.createElement("h2");
            title.textContent = "🎁 Mở Hộp Quà Ma Thuật! 🎁";
            title.style.cssText = `
                color: #fbbf24;
                font-size: 2.5rem;
                font-weight: 900;
                margin-bottom: 30px;
                text-shadow: 0 0 20px rgba(251, 191, 36, 0.8);
                animation: titleGlow 2s ease-in-out infinite;
            `;

            // Khung băng chuyền cải tiến
            const frame = document.createElement("div");
            frame.style.cssText = `
                width: 650px;
                height: 180px;
                overflow: hidden;
                border: 6px solid #fbbf24;
                border-radius: 20px;
                background: linear-gradient(135deg, #1e293b, #0f172a);
                position: relative;
                box-shadow: 0 0 30px rgba(251, 191, 36, 0.6), inset 0 0 20px rgba(0,0,0,0.5);
            `;

            // Băng chuyền với hiệu ứng mượt mà hơn
            const carousel = document.createElement("div");
            carousel.style.cssText = `
                display: flex;
                gap: 15px;
                position: absolute;
                left: 0;
                top: 25px;
                transition: transform 5s cubic-bezier(0.25, 0.46, 0.45, 0.94);
            `;

            // Hệ thống phần thưởng với độ hiếm
            const rewardsByRarity = {
                common: [
                    { emoji: "⭐", name: "Ngôi Sao Nhỏ", color: "#94a3b8", rarity: "Thường", rarityColor: "#94a3b8" },
                    { emoji: "💙", name: "Trái Tim Xanh", color: "#60a5fa", rarity: "Thường", rarityColor: "#94a3b8" },
                    { emoji: "🌙", name: "Ánh Trăng", color: "#e2e8f0", rarity: "Thường", rarityColor: "#94a3b8" }
                ],
                rare: [
                    { emoji: "💎", name: "Kim Cương Ma Thuật", color: "#06b6d4", rarity: "Hiếm", rarityColor: "#06b6d4" },
                    { emoji: "🔮", name: "Quả Cầu Thần Thánh", color: "#8b5cf6", rarity: "Hiếm", rarityColor: "#06b6d4" },
                    { emoji: "❄️", name: "Tinh Thể Băng Giá", color: "#0ea5e9", rarity: "Hiếm", rarityColor: "#06b6d4" }
                ],
                epic: [
                    { emoji: "🏆", name: "Cúp Vàng Rem", color: "#f59e0b", rarity: "Sử Thi", rarityColor: "#8b5cf6" },
                    { emoji: "🌟", name: "Ánh Sáng Vĩnh Cửu", color: "#10b981", rarity: "Sử Thi", rarityColor: "#8b5cf6" }
                ],
                legendary: [
                    { emoji: "💫", name: "Vũ Trụ Huyền Bí", color: "#ec4899", rarity: "Huyền Thoại", rarityColor: "#f59e0b" },
                    { emoji: "👑", name: "Vương Miện Rem", color: "#fbbf24", rarity: "Huyền Thoại", rarityColor: "#f59e0b" }
                ]
            };

            // Xác định độ hiếm - LUÔN LEGENDARY (100% tỷ lệ thực tế)
            const winningRarity = 'legendary';
            const winningReward = rewardsByRarity.legendary[Math.floor(Math.random() * rewardsByRarity.legendary.length)];
            
            // Chỉ hiển thị phần thưởng Huyền Thoại trên băng chuyền
            const displayRewards = rewardsByRarity.legendary;

            // Tạo 25 ảnh với phần thưởng thật ở vị trí 18
            for (let i = 0; i < 25; i++) {
                const rewardBox = document.createElement("div");
                const isWinning = i === 18;
                const reward = isWinning ? winningReward : displayRewards[Math.floor(Math.random() * displayRewards.length)];
                
                rewardBox.style.cssText = `
                    width: 130px;
                    height: 130px;
                    border-radius: 15px;
                    display: flex;
                    flex-direction: column;
                    align-items: center;
                    justify-content: center;
                    font-size: 2.5rem;
                    background: linear-gradient(135deg, ${reward.color}20, ${reward.color}40);
                    border: 3px solid ${reward.rarityColor};
                    box-shadow: 0 5px 15px ${reward.rarityColor}40;
                    flex-shrink: 0;
                    position: relative;
                    overflow: hidden;
                `;

                // Hiệu ứng lấp lánh dựa trên độ hiếm
                const shimmer = document.createElement("div");
                let shimmerIntensity = '0.3';
                if (reward.rarity === 'Huyền Thoại') shimmerIntensity = '0.8';
                else if (reward.rarity === 'Sử Thi') shimmerIntensity = '0.6';
                else if (reward.rarity === 'Hiếm') shimmerIntensity = '0.4';
                
                shimmer.style.cssText = `
                    position: absolute;
                    top: -50%;
                    left: -50%;
                    width: 200%;
                    height: 200%;
                    background: linear-gradient(45deg, transparent, rgba(255,255,255,${shimmerIntensity}), transparent);
                    animation: shimmer ${reward.rarity === 'Huyền Thoại' ? '1s' : '2s'} linear infinite;
                `;

                const emoji = document.createElement("div");
                emoji.textContent = reward.emoji;
                emoji.style.cssText = `
                    filter: drop-shadow(0 0 10px ${reward.rarityColor});
                    animation: float 3s ease-in-out infinite;
                    margin-bottom: 5px;
                `;

                // Nhãn độ hiếm
                const rarityLabel = document.createElement("div");
                rarityLabel.textContent = reward.rarity;
                rarityLabel.style.cssText = `
                    font-size: 0.7rem;
                    font-weight: 900;
                    color: ${reward.rarityColor};
                    text-shadow: 0 0 5px ${reward.rarityColor};
                    text-transform: uppercase;
                    letter-spacing: 1px;
                `;

                rewardBox.appendChild(shimmer);
                rewardBox.appendChild(emoji);
                rewardBox.appendChild(rarityLabel);
                carousel.appendChild(rewardBox);
            }

            // Vạch chỉ định với hiệu ứng đẹp hơn
            const pointer = document.createElement("div");
            pointer.style.cssText = `
                position: absolute;
                top: 0;
                left: 50%;
                transform: translateX(-50%);
                width: 6px;
                height: 100%;
                background: linear-gradient(to bottom, #ef4444, #dc2626, #ef4444);
                box-shadow: 0 0 20px #ef4444, inset 0 0 10px rgba(255,255,255,0.3);
                animation: pointerGlow 1s ease-in-out infinite;
            `;

            // Thêm mũi tên chỉ xuống
            const arrow = document.createElement("div");
            arrow.style.cssText = `
                position: absolute;
                top: -15px;
                left: 50%;
                transform: translateX(-50%);
                width: 0;
                height: 0;
                border-left: 15px solid transparent;
                border-right: 15px solid transparent;
                border-top: 20px solid #ef4444;
                filter: drop-shadow(0 0 10px #ef4444);
            `;

            frame.appendChild(carousel);
            frame.appendChild(pointer);
            frame.appendChild(arrow);
            overlay.appendChild(title);
            overlay.appendChild(frame);

            // Thêm hướng dẫn và thông tin độ hiếm
            const instruction = document.createElement("p");
            instruction.textContent = "🎵 Băng chuyền đang quay... Chờ đợi phần thưởng của bạn!";
            instruction.style.cssText = `
                color: #e2e8f0;
                font-size: 1.2rem;
                font-weight: 600;
                margin-top: 20px;
                text-align: center;
                animation: pulse 2s ease-in-out infinite;
            `;
            
            // Bảng tỷ lệ độ hiếm
            const rarityInfo = document.createElement("div");
            rarityInfo.style.cssText = `
                display: flex;
                justify-content: center;
                gap: 20px;
                margin-top: 15px;
                flex-wrap: wrap;
            `;
            
            const rarityItems = [
                { name: "Thường", color: "#94a3b8", rate: "60%" },
                { name: "Hiếm", color: "#06b6d4", rate: "25%" },
                { name: "Sử Thi", color: "#8b5cf6", rate: "12%" },
                { name: "Huyền Thoại", color: "#f59e0b", rate: "3%" }
            ];
            
            rarityItems.forEach(item => {
                const rarityItem = document.createElement("div");
                rarityItem.style.cssText = `
                    background: ${item.color}20;
                    border: 2px solid ${item.color};
                    border-radius: 10px;
                    padding: 8px 12px;
                    text-align: center;
                    backdrop-filter: blur(10px);
                `;
                
                rarityItem.innerHTML = `
                    <div style="color: ${item.color}; font-size: 0.8rem; font-weight: 900; text-transform: uppercase; letter-spacing: 1px;">${item.name}</div>
                    <div style="color: #e2e8f0; font-size: 0.7rem; font-weight: 600;">${item.rate}</div>
                `;
                
                rarityInfo.appendChild(rarityItem);
            });
            
            overlay.appendChild(instruction);
            overlay.appendChild(rarityInfo);

            document.body.appendChild(overlay);

            // Giả lập âm thanh bằng hiệu ứng thị giác
            let tickCount = 0;
            const tickInterval = setInterval(() => {
                // Hiệu ứng nhấp nháy viền
                frame.style.borderColor = tickCount % 2 === 0 ? '#fbbf24' : '#f59e0b';
                tickCount++;
            }, 100);

            // Hiệu ứng chạy băng chuyền
            setTimeout(() => {
                carousel.style.transform = "translateX(-1950px)"; // Dừng tại vị trí 18
                instruction.textContent = "🎯 Băng chuyền đang chậm lại...";
            }, 200);

            // Sau khi dừng - hiển thị kết quả
            setTimeout(() => {
                clearInterval(tickInterval);
                frame.style.borderColor = '#10b981';
                
                // winningReward đã được định nghĩa ở trên
                
                // Hiệu ứng pháo hoa
                createFireworks(overlay);
                
                // Thông báo chiến thắng với độ hiếm
                const winMessage = document.createElement("div");
                const rarityGradients = {
                    'Thường': 'linear-gradient(135deg, rgba(148, 163, 184, 0.9), rgba(100, 116, 139, 0.9))',
                    'Hiếm': 'linear-gradient(135deg, rgba(6, 182, 212, 0.9), rgba(8, 145, 178, 0.9))',
                    'Sử Thi': 'linear-gradient(135deg, rgba(139, 92, 246, 0.9), rgba(124, 58, 237, 0.9))',
                    'Huyền Thoại': 'linear-gradient(135deg, rgba(251, 191, 36, 0.9), rgba(245, 158, 11, 0.9))'
                };
                
                winMessage.style.cssText = `
                    background: ${rarityGradients[winningReward.rarity]};
                    backdrop-filter: blur(15px);
                    border: 3px solid ${winningReward.rarityColor};
                    border-radius: 20px;
                    padding: 30px;
                    margin-top: 30px;
                    text-align: center;
                    box-shadow: 0 20px 40px ${winningReward.rarityColor}40;
                    animation: bounceIn 0.8s ease-out;
                `;

                // Hiệu ứng đặc biệt cho phần thưởng huyền thoại
                if (winningReward.rarity === 'Huyền Thoại') {
                    winMessage.style.animation = 'bounceIn 0.8s ease-out, titleGlow 2s ease-in-out infinite';
                }

                winMessage.innerHTML = `
                    <div style="font-size: 4rem; margin-bottom: 15px; filter: drop-shadow(0 0 20px ${winningReward.rarityColor});">${winningReward.emoji}</div>
                    <div style="background: ${winningReward.rarityColor}; color: white; padding: 5px 15px; border-radius: 15px; display: inline-block; margin-bottom: 15px; font-size: 0.9rem; font-weight: 900; text-transform: uppercase; letter-spacing: 1px;">
                        ${winningReward.rarity}
                    </div>
                    <h3 style="color: white; font-size: 1.8rem; font-weight: 900; margin-bottom: 10px;">
                        🎉 Chúc Mừng! 🎉
                    </h3>
                    <p style="color: #e2e8f0; font-size: 1.3rem; font-weight: 600; margin-bottom: 15px;">
                        Bạn nhận được phần thưởng <span style="color: ${winningReward.rarityColor}; font-weight: 900;">${winningReward.rarity}</span>:
                    </p>
                    <p style="color: white; font-size: 1.5rem; font-weight: 900; margin-bottom: 20px; text-shadow: 0 0 10px ${winningReward.rarityColor};">
                        ${winningReward.name}
                    </p>
                `;

                const closeBtn = document.createElement("button");
                closeBtn.textContent = "✨ Tiếp Tục Ma Thuật";
                closeBtn.style.cssText = `
                    padding: 15px 30px;
                    border-radius: 15px;
                    background: linear-gradient(135deg, #8b5cf6, #7c3aed);
                    color: white;
                    border: none;
                    font-size: 1.1rem;
                    font-weight: 700;
                    cursor: pointer;
                    transition: all 0.3s ease;
                    box-shadow: 0 5px 15px rgba(139, 92, 246, 0.4);
                `;
                
                closeBtn.onmouseover = () => {
                    closeBtn.style.transform = "translateY(-2px) scale(1.05)";
                    closeBtn.style.boxShadow = "0 8px 25px rgba(139, 92, 246, 0.6)";
                };
                
                closeBtn.onmouseout = () => {
                    closeBtn.style.transform = "translateY(0) scale(1)";
                    closeBtn.style.boxShadow = "0 5px 15px rgba(139, 92, 246, 0.4)";
                };

                closeBtn.onclick = () => {
                    overlay.style.animation = "fadeOut 0.5s ease-out";
                    setTimeout(() => {
                        overlay.remove();
                        // Quay trở lại giao diện chính sau khi nhận phần thưởng
                        closeResultModal();
                    }, 500);
                };

                winMessage.appendChild(closeBtn);
                overlay.appendChild(winMessage);
                
                instruction.textContent = "🎊 Phần thưởng đã được mở khóa!";
                instruction.style.color = '#10b981';
            }, 5500);
        }

        // Tạo hiệu ứng pháo hoa
        function createFireworks(container) {
            for (let i = 0; i < 15; i++) {
                setTimeout(() => {
                    const firework = document.createElement("div");
                    firework.textContent = ["🎆", "✨", "🌟", "💫", "⭐"][Math.floor(Math.random() * 5)];
                    firework.style.cssText = `
                        position: absolute;
                        font-size: 2rem;
                        pointer-events: none;
                        left: ${Math.random() * 100}%;
                        top: ${Math.random() * 100}%;
                        animation: fireworkExplode 2s ease-out forwards;
                    `;
                    container.appendChild(firework);
                    
                    setTimeout(() => firework.remove(), 2000);
                }, i * 100);
            }
        }

        function showResult(isCorrect) {
            const resultModal = document.getElementById('resultModal');
            const resultIcon = document.getElementById('resultIcon');
            const resultTitle = document.getElementById('resultTitle');
            const resultMessage = document.getElementById('resultMessage');
            
            if (isCorrect) {
                resultIcon.textContent = '🎉';
                resultTitle.textContent = 'Ma Thuật Thành Công!';
                resultMessage.textContent = 'Rem tự hào về bạn! ❄️✨';
                resultModal.querySelector('.kawaii-content').classList.add('magic-fireworks');
                setTimeout(() => {
                    resultModal.querySelector('.kawaii-content').classList.remove('magic-fireworks');
                }, 1500);
                
                // Hiển thị hộp quà sau khi trả lời đúng
                setTimeout(() => {
                    showReward(currentQuestion);
                }, 2000);
                return; // Không hiển thị modal kết quả ngay
            } else {
                resultIcon.textContent = '😅';
                resultTitle.textContent = 'Ma Thuật Thất Bại!';
                resultMessage.textContent = 'Đừng lo, Rem sẽ giúp bạn! 💙';
            }
            
            resultModal.classList.remove('hidden');
        }

        function closeModal() {
            document.getElementById('questionModal').classList.add('hidden');
        }

        function closeResultModal() {
            document.getElementById('resultModal').classList.add('hidden');
            closeModal();
            
            if (answeredQuestions.size === 7) {
                setTimeout(() => {
                    showFinalResult();
                }, 500);
            }
        }

        function showFinalResult() {
            const resultModal = document.getElementById('resultModal');
            const resultIcon = document.getElementById('resultIcon');
            const resultTitle = document.getElementById('resultTitle');
            const resultMessage = document.getElementById('resultMessage');
            
            resultIcon.textContent = '🏆';
            resultTitle.textContent = 'Ma Thuật Hoàn Thành!';
            resultMessage.textContent = `Rem rất tự hào! Bạn đã trả lời đúng ${score}/7 câu! ${score >= 5 ? 'Xuất sắc như Rem! ❄️' : score >= 3 ? 'Tốt lắm! 💙' : 'Hãy cố gắng hơn nhé! 🌟'}`;
            
            resultModal.querySelector('.kawaii-content').classList.add('magic-fireworks');
            setTimeout(() => {
                resultModal.querySelector('.kawaii-content').classList.remove('magic-fireworks');
            }, 1500);
            
            resultModal.classList.remove('hidden');
        }

        function updateScore() {
            document.getElementById('score').textContent = `${score}/7`;
        }

        function updateProgress() {
            const progress = (answeredQuestions.size / 7) * 100;
            document.getElementById('progress').style.width = progress + '%';
        }

        // Initialize effects
        createSnowfall();
        createIceParticles();
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'97cee6840745166a',t:'MTc1NzUwNzA0Ny4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
