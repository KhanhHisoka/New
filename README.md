<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🌌 Trường Hấp Dẫn - Khám Phá Vật Lý Vũ Trụ</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@300;400;700;900&display=swap');
        
        * {
            font-family: 'Noto Sans JP', sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, 
                #0f0f23 0%, 
                #1a1a3e 25%, 
                #2d1b69 50%, 
                #1a1a3e 75%, 
                #0f0f23 100%);
            background-size: 400% 400%;
            animation: spaceFlow 20s ease-in-out infinite;
            position: relative;
            overflow: hidden;
            height: 100vh;
            margin: 0;
            padding: 0;
        }
        
        @keyframes spaceFlow {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }
        
        /* Planet Effects */
        @keyframes planetOrbit {
            0% { transform: translateY(0px) rotate(0deg); }
            25% { transform: translateY(-3px) rotate(90deg); }
            50% { transform: translateY(0px) rotate(180deg); }
            75% { transform: translateY(3px) rotate(270deg); }
            100% { transform: translateY(0px) rotate(360deg); }
        }
        
        @keyframes planetGlow {
            0%, 100% { 
                box-shadow: 0 0 15px rgba(168, 85, 247, 0.6), 
                           0 0 30px rgba(124, 58, 237, 0.4);
            }
            50% { 
                box-shadow: 0 0 25px rgba(168, 85, 247, 0.8), 
                           0 0 50px rgba(124, 58, 237, 0.6);
            }
        }
        
        @keyframes gravityPull {
            0%, 20%, 50%, 80%, 100% { transform: translateY(0) scale(1); }
            40% { transform: translateY(-8px) scale(1.1); }
            60% { transform: translateY(-4px) scale(1.05); }
        }
        
        .planet {
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            cursor: pointer;
            position: relative;
            border: 2px solid rgba(168, 85, 247, 0.4);
            backdrop-filter: blur(20px);
            animation: planetOrbit 12s ease-in-out infinite;
            background: radial-gradient(circle at 30% 30%, 
                rgba(255, 255, 255, 0.3), 
                rgba(168, 85, 247, 0.2), 
                rgba(124, 58, 237, 0.4));
            box-shadow: 0 0 15px rgba(168, 85, 247, 0.3);
        }
        
        .planet:hover {
            animation: gravityPull 0.8s ease-in-out;
            transform: scale(1.15);
            box-shadow: 0 15px 30px rgba(168, 85, 247, 0.5);
        }
        
        .planet.completed {
            animation: planetGlow 2s infinite, planetOrbit 12s ease-in-out infinite;
            border-color: rgba(34, 197, 94, 0.8);
            box-shadow: 0 0 20px rgba(34, 197, 94, 0.6);
        }
        
        /* Cosmic Modal Styling */
        .cosmic-modal {
            backdrop-filter: blur(25px);
            background: rgba(15, 15, 35, 0.9);
        }
        
        .cosmic-content {
            background: linear-gradient(135deg, 
                rgba(30, 30, 60, 0.95), 
                rgba(45, 27, 105, 0.9),
                rgba(26, 26, 62, 0.95));
            backdrop-filter: blur(20px);
            border: 3px solid rgba(168, 85, 247, 0.4);
            box-shadow: 0 25px 50px rgba(124, 58, 237, 0.4);
        }
        
        /* Enhanced Cosmic Button Styling */
        .cosmic-btn {
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            background: linear-gradient(135deg, 
                rgba(30, 30, 60, 0.9), 
                rgba(45, 27, 105, 0.8),
                rgba(26, 26, 62, 0.9));
            border: 3px solid transparent;
            background-clip: padding-box;
            backdrop-filter: blur(20px);
            position: relative;
            overflow: hidden;
            color: #e2e8f0;
            box-shadow: 
                0 8px 25px rgba(0, 0, 0, 0.3),
                0 0 0 1px rgba(168, 85, 247, 0.3);
        }
        
        .cosmic-btn:hover {
            transform: translateY(-3px) scale(1.02);
            box-shadow: 
                0 15px 30px rgba(168, 85, 247, 0.4),
                0 0 20px rgba(124, 58, 237, 0.6);
            background: linear-gradient(135deg, 
                rgba(45, 27, 105, 1), 
                rgba(30, 30, 60, 0.95),
                rgba(26, 26, 62, 1));
            color: #f8fafc;
        }
        
        .cosmic-btn:active {
            transform: translateY(-1px) scale(1.01);
        }
        
        /* Letter styling for A, B, C, D */
        .option-letter {
            display: inline-block;
            width: 28px;
            height: 28px;
            border-radius: 50%;
            background: linear-gradient(135deg, #a855f7, #7c3aed);
            color: white;
            font-weight: 900;
            font-size: 0.9rem;
            line-height: 28px;
            text-align: center;
            margin-right: 10px;
            box-shadow: 0 4px 15px rgba(168, 85, 247, 0.4);
            transition: all 0.3s ease;
        }
        
        .cosmic-btn:hover .option-letter {
            background: linear-gradient(135deg, #7c3aed, #6366f1);
            box-shadow: 0 6px 20px rgba(124, 58, 237, 0.6);
            transform: scale(1.1);
        }
        
        /* Enhanced Magic Effects */
        .correct-magic {
            background: linear-gradient(135deg, #10b981, #059669, #047857) !important;
            animation: correctPulse 1.2s ease-out;
            color: white !important;
            box-shadow: 
                0 0 30px rgba(16, 185, 129, 0.8),
                0 0 60px rgba(5, 150, 105, 0.6) !important;
        }
        
        .correct-magic .option-letter {
            background: linear-gradient(135deg, #047857, #065f46) !important;
            box-shadow: 0 0 20px rgba(16, 185, 129, 0.8) !important;
        }
        
        .incorrect-magic {
            background: linear-gradient(135deg, #ef4444, #dc2626, #b91c1c) !important;
            animation: incorrectShake 0.6s ease-out;
            color: white !important;
            box-shadow: 
                0 0 30px rgba(239, 68, 68, 0.8),
                0 0 60px rgba(220, 38, 38, 0.6) !important;
        }
        
        .incorrect-magic .option-letter {
            background: linear-gradient(135deg, #b91c1c, #991b1b) !important;
            box-shadow: 0 0 20px rgba(239, 68, 68, 0.8) !important;
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
        
        /* Cosmic Progress Bar */
        .cosmic-progress {
            background: rgba(30, 30, 60, 0.4);
            backdrop-filter: blur(15px);
            border: 2px solid rgba(168, 85, 247, 0.3);
        }
        
        .progress-cosmic {
            background: linear-gradient(90deg, #a855f7, #7c3aed, #6366f1, #8b5cf6);
            box-shadow: 0 0 20px rgba(168, 85, 247, 0.6);
            animation: cosmicGlow 3s ease-in-out infinite;
        }
        
        @keyframes cosmicGlow {
            0%, 100% { box-shadow: 0 0 20px rgba(168, 85, 247, 0.6); }
            50% { box-shadow: 0 0 30px rgba(168, 85, 247, 0.8); }
        }
        
        /* Cosmic Score Display */
        .cosmic-score {
            background: linear-gradient(135deg, 
                rgba(45, 27, 105, 0.6), 
                rgba(30, 30, 60, 0.7));
            backdrop-filter: blur(20px);
            border: 2px solid rgba(168, 85, 247, 0.5);
            border-radius: 20px;
            padding: 6px 16px;
            display: inline-block;
            box-shadow: 0 8px 25px rgba(124, 58, 237, 0.3);
        }
        
        /* Cosmic Title Glow */
        .cosmic-title {
            animation: cosmicTitle 5s ease-in-out infinite;
            text-shadow: 0 0 20px rgba(168, 85, 247, 0.8);
        }
        
        @keyframes cosmicTitle {
            0%, 100% { 
                text-shadow: 0 0 20px rgba(168, 85, 247, 0.8), 
                           0 0 40px rgba(124, 58, 237, 0.6); 
            }
            50% { 
                text-shadow: 0 0 30px rgba(168, 85, 247, 1), 
                           0 0 60px rgba(124, 58, 237, 0.8); 
            }
        }
        
        /* Fireworks Effect */
        .magic-fireworks {
            position: relative;
        }
        
        .magic-fireworks::before {
            content: '✨💫⭐🌟💎';
            position: absolute;
            top: -30px;
            left: 50%;
            transform: translateX(-50%);
            font-size: 1.5rem;
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
        
        @keyframes shimmer {
            0% { transform: translateX(-100%) translateY(-100%) rotate(45deg); }
            100% { transform: translateX(100%) translateY(100%) rotate(45deg); }
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
        }
    </style>
</head>
<body class="text-white">
    <div class="h-screen flex flex-col justify-center px-4 py-2 relative z-10">
        <!-- Cosmic Header -->
        <div class="text-center mb-4 relative">
            <h1 class="text-3xl font-black mb-2 bg-gradient-to-r from-purple-300 via-blue-300 to-indigo-300 bg-clip-text text-transparent cosmic-title" style="font-weight: 900;">
                🌌 Trường Hấp Dẫn Vũ Trụ 🌌
            </h1>
            <div class="relative inline-block">
                <p class="text-base font-black text-purple-200 mb-2 drop-shadow-lg" style="font-weight: 900; text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);">
                    🪐 Khám phá các hành tinh để tìm hiểu về lực hấp dẫn! 🪐
                </p>
            </div>
            <div class="cosmic-score mt-2">
                <span class="text-sm font-black text-purple-200" style="font-weight: 900;">🌟 Điểm: </span>
                <span id="score" class="text-lg font-black text-white" style="font-weight: 900;">0/7</span>
            </div>
        </div>

        <!-- Cosmic Planets -->
        <div class="flex flex-col items-center justify-center flex-1 space-y-4">
            <!-- Top Row - 4 Planets -->
            <div class="flex justify-center items-center gap-4">
                <!-- Planet 1 - Mercury -->
                <div class="planet w-16 h-16 bg-gradient-to-br from-orange-400 to-red-500 rounded-full flex items-center justify-center text-2xl font-bold shadow-lg" 
                     onclick="openQuestion(0)">
                    <span>☿️</span>
                </div>
                
                <!-- Planet 2 - Venus -->
                <div class="planet w-16 h-16 bg-gradient-to-br from-yellow-400 to-orange-500 rounded-full flex items-center justify-center text-2xl font-bold shadow-lg" 
                     onclick="openQuestion(1)">
                    <span>♀️</span>
                </div>
                
                <!-- Planet 3 - Earth -->
                <div class="planet w-16 h-16 bg-gradient-to-br from-blue-400 to-green-500 rounded-full flex items-center justify-center text-2xl font-bold shadow-lg" 
                     onclick="openQuestion(2)">
                    <span>🌍</span>
                </div>
                
                <!-- Planet 4 - Mars -->
                <div class="planet w-16 h-16 bg-gradient-to-br from-red-500 to-red-700 rounded-full flex items-center justify-center text-2xl font-bold shadow-lg" 
                     onclick="openQuestion(3)">
                    <span>♂️</span>
                </div>
            </div>
            
            <!-- Bottom Row - 3 Planets -->
            <div class="flex justify-center items-center gap-4">
                <!-- Planet 5 - Jupiter -->
                <div class="planet w-16 h-16 bg-gradient-to-br from-yellow-600 to-orange-700 rounded-full flex items-center justify-center text-2xl font-bold shadow-lg" 
                     onclick="openQuestion(4)">
                    <span>♃</span>
                </div>
                
                <!-- Planet 6 - Saturn -->
                <div class="planet w-16 h-16 bg-gradient-to-br from-yellow-500 to-yellow-700 rounded-full flex items-center justify-center text-2xl font-bold shadow-lg" 
                     onclick="openQuestion(5)">
                    <span>♄</span>
                </div>
                
                <!-- Planet 7 - Neptune -->
                <div class="planet w-16 h-16 bg-gradient-to-br from-blue-600 to-blue-800 rounded-full flex items-center justify-center text-2xl font-bold shadow-lg" 
                     onclick="openQuestion(6)">
                    <span>♆</span>
                </div>
            </div>
        </div>

        <!-- Cosmic Progress Bar -->
        <div class="flex flex-col items-center justify-center max-w-md mx-auto mt-4">
            <div class="text-center mb-2">
                <span class="text-sm font-black text-purple-200" style="font-weight: 900;">🚀 Tiến Độ Khám Phá</span>
            </div>
            <div class="cosmic-progress rounded-full h-4 p-1 w-full">
                <div id="progress" class="progress-cosmic h-2 rounded-full transition-all duration-700 ease-out" style="width: 0%"></div>
            </div>
        </div>
    </div>

    <!-- Cosmic Question Modal -->
    <div id="questionModal" class="fixed inset-0 cosmic-modal hidden flex items-center justify-center z-50 p-4">
        <div class="cosmic-content text-white rounded-3xl p-6 max-w-2xl w-full mx-auto relative flex flex-col items-center">
            <div class="absolute top-4 right-4">
                <span class="text-2xl">🌌</span>
            </div>
            <div class="text-center mb-6 w-full">
                <h2 class="text-2xl font-black mb-3 text-purple-300" style="font-weight: 900;">
                    🪐 Khám Phá Hành Tinh <span id="questionNumber"></span>
                </h2>
                <p id="questionText" class="text-lg font-bold leading-relaxed text-gray-200" style="font-weight: 700;"></p>
            </div>
            
            <div class="space-y-3 w-full">
                <button class="cosmic-btn w-full p-4 text-left rounded-xl font-bold text-base flex items-center" onclick="selectAnswer(0)" style="font-weight: 700;">
                    <span class="option-letter">A</span>
                    <span id="answerA" class="flex-1"></span>
                </button>
                <button class="cosmic-btn w-full p-4 text-left rounded-xl font-bold text-base flex items-center" onclick="selectAnswer(1)" style="font-weight: 700;">
                    <span class="option-letter">B</span>
                    <span id="answerB" class="flex-1"></span>
                </button>
                <button class="cosmic-btn w-full p-4 text-left rounded-xl font-bold text-base flex items-center" onclick="selectAnswer(2)" style="font-weight: 700;">
                    <span class="option-letter">C</span>
                    <span id="answerC" class="flex-1"></span>
                </button>
                <button class="cosmic-btn w-full p-4 text-left rounded-xl font-bold text-base flex items-center" onclick="selectAnswer(3)" style="font-weight: 700;">
                    <span class="option-letter">D</span>
                    <span id="answerD" class="flex-1"></span>
                </button>
            </div>
            
            <div class="mt-6 text-center">
                <button onclick="closeModal()" class="px-6 py-2 bg-gradient-to-r from-red-500 to-red-600 text-white rounded-lg hover:from-red-600 hover:to-red-700 transition-all duration-300 font-semibold">
                    ❌ Đóng
                </button>
            </div>
        </div>
    </div>

    <!-- Result Modal -->
    <div id="resultModal" class="fixed inset-0 cosmic-modal hidden flex items-center justify-center z-50 p-4">
        <div class="cosmic-content text-white rounded-3xl p-8 max-w-md w-full mx-auto text-center relative flex flex-col items-center justify-center">
            <div id="resultIcon" class="text-6xl mb-4"></div>
            <h3 id="resultTitle" class="text-2xl font-black mb-3" style="font-weight: 900;"></h3>
            <p id="resultMessage" class="text-lg mb-6 font-bold" style="font-weight: 700;"></p>
            <button onclick="closeResultModal()" class="px-6 py-3 bg-gradient-to-r from-blue-500 to-purple-600 text-white rounded-xl hover:from-blue-600 hover:to-purple-700 transition-all duration-300 font-bold text-base shadow-lg">
                ✨ Tiếp Tục
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

        function openQuestion(questionIndex) {
            if (answeredQuestions.has(questionIndex)) {
                return;
            }
            
            currentQuestion = questionIndex;
            const q = questions[questionIndex];
            
            document.getElementById('questionNumber').textContent = questionIndex + 1;
            document.getElementById('questionText').textContent = q.question;
            document.getElementById('answerA').textContent = q.answers[0];
            document.getElementById('answerB').textContent = q.answers[1];
            document.getElementById('answerC').textContent = q.answers[2];
            document.getElementById('answerD').textContent = q.answers[3];
            
            // Reset answer buttons
            const buttons = document.querySelectorAll('.cosmic-btn');
            buttons.forEach(btn => {
                btn.className = 'cosmic-btn w-full p-4 text-left rounded-xl font-bold text-base flex items-center';
                btn.disabled = false;
            });
            
            document.getElementById('questionModal').classList.remove('hidden');
        }

        function selectAnswer(answerIndex) {
            const q = questions[currentQuestion];
            const buttons = document.querySelectorAll('.cosmic-btn');
            
            buttons.forEach(btn => btn.disabled = true);
            
            buttons[q.correct].classList.add('correct-magic');
            
            let isCorrect = false;
            if (answerIndex === q.correct) {
                isCorrect = true;
                score++;
                document.querySelector('.cosmic-content').classList.add('magic-fireworks');
                setTimeout(() => {
                    document.querySelector('.cosmic-content').classList.remove('magic-fireworks');
                }, 1500);
            } else {
                buttons[answerIndex].classList.add('incorrect-magic');
            }
            
            answeredQuestions.add(currentQuestion);
            
            const planets = document.querySelectorAll('.planet');
            planets[currentQuestion].classList.add('completed');
            
            updateScore();
            updateProgress();
            
            setTimeout(() => {
                showResult(isCorrect);
            }, 1500);
        }

        // 🎁 Hiệu ứng mở hộp quà với băng chuyền
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
            title.textContent = "🎁 Quay Thưởng Ma Thuật! 🎁";
            title.style.cssText = `
                color: #fbbf24;
                font-size: 2.5rem;
                font-weight: 900;
                margin-bottom: 30px;
                text-shadow: 0 0 20px rgba(251, 191, 36, 0.8);
                animation: titleGlow 2s ease-in-out infinite;
            `;

            // Khung băng chuyền
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

            // Băng chuyền
            const carousel = document.createElement("div");
            carousel.style.cssText = `
                display: flex;
                gap: 15px;
                position: absolute;
                left: 0;
                top: 25px;
                transition: transform 5s cubic-bezier(0.25, 0.46, 0.45, 0.94);
            `;

            // Hệ thống phần thưởng Huyền Thoại
            const rewards = [
                { 
                    name: "Poro The Destroyer", 
                    image: "https://drive.google.com/uc?export=view&id=1IJB9l6a_saKiSYlU96eLuNl5VzCr8fdH", 
                    color: "#ec4899", 
                    rarity: "Huyền Thoại", 
                    rarityColor: "#f59e0b", 
                    weight: 50 
                },
                { 
                    name: "Daisy The Murder", 
                    image: "https://drive.google.com/uc?export=view&id=1V9TA6v_vKU5LmvoqlZjKy0xNqC5wmYrw", 
                    color: "#8b5cf6", 
                    rarity: "Huyền Thoại", 
                    rarityColor: "#f59e0b", 
                    weight: 50 
                }
            ];

            // Tạo pool phần thưởng theo tỷ lệ
            function createWeightedRewardPool() {
                const pool = [];
                rewards.forEach(reward => {
                    for (let i = 0; i < reward.weight; i++) {
                        pool.push(reward);
                    }
                });
                return pool;
            }

            const rewardPool = createWeightedRewardPool();

            // Tạo 25 ảnh với phân bố theo tỷ lệ
            for (let i = 0; i < 25; i++) {
                const rewardBox = document.createElement("div");
                const reward = rewardPool[Math.floor(Math.random() * rewardPool.length)];
                
                rewardBox.style.cssText = `
                    width: 130px;
                    height: 130px;
                    border-radius: 15px;
                    display: flex;
                    flex-direction: column;
                    align-items: center;
                    justify-content: center;
                    background: linear-gradient(135deg, ${reward.color}20, ${reward.color}40);
                    border: 3px solid ${reward.rarityColor};
                    box-shadow: 0 5px 15px ${reward.rarityColor}40;
                    flex-shrink: 0;
                    position: relative;
                    overflow: hidden;
                `;

                // Hiệu ứng lấp lánh
                const shimmer = document.createElement("div");
                shimmer.style.cssText = `
                    position: absolute;
                    top: -50%;
                    left: -50%;
                    width: 200%;
                    height: 200%;
                    background: linear-gradient(45deg, transparent, rgba(255,255,255,0.8), transparent);
                    animation: shimmer 1s linear infinite;
                `;

                // Hiển thị hình ảnh hoặc emoji fallback
                if (reward.image && reward.image.startsWith('http')) {
                    const rewardDisplay = document.createElement("img");
                    rewardDisplay.src = reward.image;
                    rewardDisplay.alt = reward.name;
                    rewardDisplay.style.cssText = `
                        width: 80px;
                        height: 80px;
                        object-fit: cover;
                        border-radius: 10px;
                        filter: drop-shadow(0 0 10px ${reward.rarityColor});
                        animation: float 3s ease-in-out infinite;
                        margin-bottom: 5px;
                        border: 2px solid ${reward.rarityColor};
                    `;
                    rewardDisplay.onerror = function() {
                        this.style.display = 'none';
                        const fallback = document.createElement("div");
                        fallback.textContent = reward.name === "Poro The Destroyer" ? "🐾" : "🌸";
                        fallback.style.cssText = `
                            font-size: 3rem;
                            filter: drop-shadow(0 0 10px ${reward.rarityColor});
                            animation: float 3s ease-in-out infinite;
                            margin-bottom: 5px;
                        `;
                        this.parentNode.insertBefore(fallback, this);
                    };
                    rewardBox.appendChild(rewardDisplay);
                } else {
                    const fallback = document.createElement("div");
                    fallback.textContent = reward.name === "Poro The Destroyer" ? "🐾" : "🌸";
                    fallback.style.cssText = `
                        font-size: 3rem;
                        filter: drop-shadow(0 0 10px ${reward.rarityColor});
                        animation: float 3s ease-in-out infinite;
                        margin-bottom: 5px;
                    `;
                    rewardBox.appendChild(fallback);
                }

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
                rewardBox.appendChild(rarityLabel);
                carousel.appendChild(rewardBox);
            }

            // Vạch chỉ định
            const pointer = document.createElement("div");
            pointer.style.cssText = `
                position: absolute;
                top: 0;
                left: 50%;
                transform: translateX(-50%);
                width: 6px;
                height: 100%;
                background: linear-gradient(to bottom, #ef4444, #dc2626, #ef4444);
                box-shadow: 0 0 20px #ef4444;
                animation: pulse 1s ease-in-out infinite;
            `;

            // Mũi tên chỉ xuống
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

            // Hướng dẫn
            const instruction = document.createElement("p");
            instruction.textContent = "🎵 Băng chuyền đang quay... Chờ đợi phần thưởng!";
            instruction.style.cssText = `
                color: #e2e8f0;
                font-size: 1.2rem;
                font-weight: 600;
                margin-top: 20px;
                text-align: center;
                animation: pulse 2s ease-in-out infinite;
            `;
            
            overlay.appendChild(instruction);
            document.body.appendChild(overlay);

            // Hiệu ứng âm thanh bằng thị giác
            let tickCount = 0;
            const tickInterval = setInterval(() => {
                frame.style.borderColor = tickCount % 2 === 0 ? '#fbbf24' : '#f59e0b';
                tickCount++;
            }, 100);

            // Chạy băng chuyền
            setTimeout(() => {
                carousel.style.transform = "translateX(-1950px)";
                instruction.textContent = "🎯 Băng chuyền đang chậm lại...";
            }, 200);

            // Hiển thị kết quả
            setTimeout(() => {
                clearInterval(tickInterval);
                frame.style.borderColor = '#10b981';
                
                // Tạo pháo hoa
                createFireworks(overlay);
                
                // Lấy phần thưởng theo tỷ lệ
                const winningReward = rewardPool[Math.floor(Math.random() * rewardPool.length)];
                
                // Thông báo chiến thắng
                const winMessage = document.createElement("div");
                winMessage.style.cssText = `
                    background: linear-gradient(135deg, rgba(251, 191, 36, 0.9), rgba(245, 158, 11, 0.9));
                    backdrop-filter: blur(15px);
                    border: 3px solid ${winningReward.rarityColor};
                    border-radius: 20px;
                    padding: 30px;
                    margin-top: 30px;
                    text-align: center;
                    box-shadow: 0 20px 40px ${winningReward.rarityColor}40;
                    animation: bounceIn 0.8s ease-out;
                `;

                // Hiển thị hình ảnh thắng thưởng
                if (winningReward.image && winningReward.image.startsWith('http')) {
                    const winEmoji = document.createElement("img");
                    winEmoji.src = winningReward.image;
                    winEmoji.alt = winningReward.name;
                    winEmoji.style.cssText = `
                        width: 120px;
                        height: 120px;
                        object-fit: cover;
                        border-radius: 15px;
                        margin-bottom: 15px;
                        filter: drop-shadow(0 0 20px ${winningReward.rarityColor});
                        border: 3px solid ${winningReward.rarityColor};
                    `;
                    winEmoji.onerror = function() {
                        this.style.display = 'none';
                        const fallback = document.createElement("div");
                        fallback.textContent = winningReward.name === "Poro The Destroyer" ? "🐾" : "🌸";
                        fallback.style.cssText = `
                            font-size: 4rem;
                            margin-bottom: 15px;
                            filter: drop-shadow(0 0 20px ${winningReward.rarityColor});
                        `;
                        this.parentNode.insertBefore(fallback, this);
                    };
                    winMessage.appendChild(winEmoji);
                } else {
                    const fallback = document.createElement("div");
                    fallback.textContent = winningReward.name === "Poro The Destroyer" ? "🐾" : "🌸";
                    fallback.style.cssText = `
                        font-size: 4rem;
                        margin-bottom: 15px;
                        filter: drop-shadow(0 0 20px ${winningReward.rarityColor});
                    `;
                    winMessage.appendChild(fallback);
                }

                const rarityBadge = document.createElement("div");
                rarityBadge.style.cssText = `
                    background: ${winningReward.rarityColor};
                    color: white;
                    padding: 5px 15px;
                    border-radius: 15px;
                    display: inline-block;
                    margin-bottom: 15px;
                    font-size: 0.9rem;
                    font-weight: 900;
                    text-transform: uppercase;
                    letter-spacing: 1px;
                `;
                rarityBadge.textContent = winningReward.rarity;

                const congratsTitle = document.createElement("h3");
                congratsTitle.textContent = "🎉 Chúc Mừng! 🎉";
                congratsTitle.style.cssText = `
                    color: white;
                    font-size: 1.8rem;
                    font-weight: 900;
                    margin-bottom: 10px;
                `;

                const rewardText = document.createElement("p");
                rewardText.innerHTML = `
                    Bạn nhận được: <span style="color: ${winningReward.rarityColor}; font-weight: 900;">${winningReward.rarity}</span>
                `;
                rewardText.style.cssText = `
                    color: #e2e8f0;
                    font-size: 1.3rem;
                    font-weight: 600;
                    margin-bottom: 15px;
                `;

                const rewardName = document.createElement("p");
                rewardName.textContent = winningReward.name;
                rewardName.style.cssText = `
                    color: white;
                    font-size: 1.5rem;
                    font-weight: 900;
                    margin-bottom: 20px;
                    text-shadow: 0 0 10px ${winningReward.rarityColor};
                `;

                const closeBtn = document.createElement("button");
                closeBtn.textContent = "✨ Tiếp Tục";
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
                        closeResultModal();
                    }, 500);
                };

                winMessage.appendChild(rarityBadge);
                winMessage.appendChild(congratsTitle);
                winMessage.appendChild(rewardText);
                winMessage.appendChild(rewardName);
                winMessage.appendChild(closeBtn);
                overlay.appendChild(winMessage);
                
                instruction.textContent = `🎊 ${winningReward.name} đã được mở khóa!`;
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
            const continueBtn = resultModal.querySelector('button');
            
            if (isCorrect) {
                resultIcon.textContent = '🎉';
                resultTitle.textContent = 'Chính Xác!';
                resultMessage.textContent = 'Bạn đã trả lời đúng! 🌟';
                
                // Thay đổi nút thành "Quay Thưởng"
                continueBtn.innerHTML = '🎰 Quay Thưởng Ma Thuật';
                continueBtn.onclick = () => {
                    showReward(currentQuestion);
                };
                
                resultModal.querySelector('.cosmic-content').classList.add('magic-fireworks');
                setTimeout(() => {
                    resultModal.querySelector('.cosmic-content').classList.remove('magic-fireworks');
                }, 1500);
            } else {
                resultIcon.textContent = '😅';
                resultTitle.textContent = 'Chưa Đúng!';
                resultMessage.textContent = 'Đừng lo, hãy thử lại! 💪';
                
                // Khôi phục nút bình thường
                continueBtn.innerHTML = '✨ Tiếp Tục';
                continueBtn.onclick = closeResultModal;
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
            resultTitle.textContent = 'Hoàn Thành!';
            resultMessage.textContent = `Bạn đã trả lời đúng ${score}/7 câu! ${score >= 5 ? 'Xuất sắc! 🌟' : score >= 3 ? 'Tốt lắm! 👍' : 'Hãy cố gắng hơn! 💪'}`;
            
            resultModal.querySelector('.cosmic-content').classList.add('magic-fireworks');
            setTimeout(() => {
                resultModal.querySelector('.cosmic-content').classList.remove('magic-fireworks');
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
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'97e7d6d927ef1055',t:'MTc1Nzc2ODU0OS4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
