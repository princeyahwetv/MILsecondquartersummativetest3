<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Table Setting and Customer Service Quiz</title>
    <style>
        body {
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            padding: 0;
            background: linear-gradient(135deg, #98FB98 0%, #00FA9A 100%);
            min-height: 100%;
        }
        
        html, body {
            height: 100%;
        }
        
        .container {
            max-width: 800px;
            margin: 0 auto;
            padding: 20px;
            min-height: 100%;
            display: flex;
            flex-direction: column;
        }
        
        .card {
            background: white;
            border-radius: 15px;
            padding: 30px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            margin-bottom: 20px;
        }
        
        .dashboard {
            background: linear-gradient(135deg, #98FB98 0%, #00FA9A 100%);
            color: white;
            text-align: center;
        }
        
        .profile-info {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
            margin-top: 20px;
        }
        
        .info-item {
            background: rgba(255,255,255,0.2);
            padding: 15px;
            border-radius: 10px;
            backdrop-filter: blur(10px);
        }
        
        .timer {
            font-size: 2em;
            font-weight: bold;
            color: #ff6b6b;
            text-align: center;
            margin: 20px 0;
            padding: 15px;
            background: #fff3cd;
            border-radius: 10px;
            border: 2px solid #ffeaa7;
        }
        
        .question-card {
            position: relative;
            overflow: hidden;
        }
        
        .question-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 25px;
            padding-bottom: 15px;
            border-bottom: 2px solid #e9ecef;
        }
        
        .question-number {
            background: linear-gradient(45deg, #FF6B6B, #4ECDC4, #45B7D1);
            color: white;
            padding: 10px 20px;
            border-radius: 25px;
            font-weight: bold;
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
        }
        
        .question-text {
            font-size: 1.3em;
            font-weight: 600;
            margin-bottom: 25px;
            color: #2d3436;
            line-height: 1.5;
        }
        
        .choices {
            display: grid;
            gap: 15px;
        }
        
        .choice {
            padding: 18px 25px;
            border: 2px solid #e9ecef;
            border-radius: 12px;
            cursor: pointer;
            transition: all 0.3s ease;
            background: #f8f9fa;
            font-size: 1.1em;
        }
        
        .choice:hover {
            border-color: #FFD700;
            background: #fff8dc;
            transform: translateY(-2px);
        }
        
        .choice.selected {
            background: #FFD700;
            color: white;
            border-color: #667eea;
        }
        
        .choice.correct {
            background: #00b894;
            border-color: #00b894;
            color: white;
        }
        
        .choice.incorrect {
            background: #e17055;
            border-color: #e17055;
            color: white;
        }
        
        .btn {
            padding: 15px 30px;
            border: none;
            border-radius: 8px;
            font-size: 1.1em;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            text-decoration: none;
            display: inline-block;
            text-align: center;
        }
        
        .btn-primary {
            background: linear-gradient(45deg, #FF6B6B, #4ECDC4);
            color: white;
            border: none;
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
        }
        
        .btn-primary:hover {
            background: linear-gradient(45deg, #4ECDC4, #45B7D1);
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(0,0,0,0.3);
        }
        
        .btn-success {
            background: #00b894;
            color: white;
        }
        
        .btn-success:hover {
            background: #00a085;
        }
        
        .btn-danger {
            background: #e17055;
            color: white;
        }
        
        .btn-danger:hover {
            background: #d63031;
        }
        
        .btn-youtube {
            background: #ff0000;
            color: white;
        }
        
        .btn-youtube:hover {
            background: #cc0000;
        }
        
        .results {
            text-align: center;
        }
        
        .score {
            font-size: 3em;
            font-weight: bold;
            margin: 20px 0;
        }
        
        .score.pass {
            color: #00b894;
        }
        
        .score.fail {
            color: #e17055;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: #2d3436;
        }
        
        .form-group input {
            width: 100%;
            padding: 12px 15px;
            border: 2px solid #e9ecef;
            border-radius: 8px;
            font-size: 1em;
            transition: border-color 0.3s ease;
        }
        
        .form-group input:focus {
            outline: none;
            border-color: #FFD700;
        }
        
        .hidden {
            display: none;
        }
        
        .progress-bar {
            width: 100%;
            height: 8px;
            background: #e9ecef;
            border-radius: 4px;
            overflow: hidden;
            margin-bottom: 20px;
        }
        
        .progress-fill {
            height: 100%;
            background: linear-gradient(90deg, #FF6B6B 0%, #4ECDC4 25%, #45B7D1 50%, #96CEB4 75%, #FFEAA7 100%);
            transition: width 0.3s ease;
        }
        
        .bonus-time {
            position: absolute;
            top: 20px;
            right: 20px;
            background: #00b894;
            color: white;
            padding: 10px 15px;
            border-radius: 20px;
            font-weight: bold;
            animation: bounceIn 0.5s ease;
        }
        
        @keyframes bounceIn {
            0% { transform: scale(0); }
            50% { transform: scale(1.2); }
            100% { transform: scale(1); }
        }
        
        .feedback {
            margin-top: 20px;
            padding: 15px;
            border-radius: 8px;
            font-weight: 600;
        }
        
        .feedback.correct {
            background: #d4edda;
            color: #155724;
            border: 1px solid #c3e6cb;
        }
        
        .feedback.incorrect {
            background: #f8d7da;
            color: #721c24;
            border: 1px solid #f5c6cb;
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Student Registration -->
        <div id="registration" class="card">
            <h1 style="text-align: center; color: #8A2BE2; margin-bottom: 30px;">📚 MIL 2nd Quarter SUMMATIVE TEST 3</h1>
            <form id="studentForm">
                <div class="form-group">
                    <label for="studentName">Student Name:</label>
                    <input type="text" id="studentName" required>
                </div>
                <div class="form-group">
                    <label for="studentGrade">Grade:</label>
                    <input type="text" id="studentGrade" required>
                </div>
                <div class="form-group">
                    <label for="studentSection">Section:</label>
                    <input type="text" id="studentSection" required>
                </div>
                <button type="submit" class="btn btn-primary" style="width: 100%;">Start Quiz</button>
            </form>
        </div>

        <!-- Dashboard -->
        <div id="dashboard" class="card dashboard hidden">
            <h2>📊 Student Dashboard</h2>
            <div class="profile-info">
                <div class="info-item">
                    <strong>Name:</strong><br>
                    <span id="displayName"></span>
                </div>
                <div class="info-item">
                    <strong>Grade:</strong><br>
                    <span id="displayGrade"></span>
                </div>
                <div class="info-item">
                    <strong>Section:</strong><br>
                    <span id="displaySection"></span>
                </div>
            </div>
        </div>

        <!-- Quiz Interface -->
        <div id="quizInterface" class="hidden">
            <div class="timer" id="timer">⏰ 5:00</div>
            
            <div class="progress-bar">
                <div class="progress-fill" id="progressFill" style="width: 0%"></div>
            </div>
            
            <div class="card question-card">
                <div id="bonusTime" class="bonus-time hidden">+5 seconds! 🎉</div>
                
                <div class="question-header">
                    <div class="question-number" id="questionNumber">Question 1 of 20</div>
                    <div style="font-weight: 600; color: #FFD700;">Score: <span id="currentScore">0</span>/15</div>
                </div>
                
                <div class="question-text" id="questionText"></div>
                
                <div class="choices" id="choices"></div>
                
                <div id="feedback" class="feedback hidden"></div>
                
                <button id="nextBtn" class="btn btn-primary hidden" style="margin-top: 20px; width: 100%;">Next Question</button>
            </div>
        </div>

        <!-- Results -->
        <div id="results" class="card results hidden">
            <h2>🎯 Quiz Results</h2>
            <div class="score" id="finalScore"></div>
            <div id="resultMessage"></div>
            <div id="resultActions" style="margin-top: 30px;"></div>
        </div>
    </div>

    <script>
        const questions = [
            {
                question: "What does People Media refer to?",
                choices: ["People who serve as channels of information and knowledge", "People who use media for entertainment purposes only", "People who create advertisements", "People who study communication theories"],
                correct: 0
            },
            {
                question: "Which of the following best describes People as Media?",
                choices: ["People who own and control mass media outlets", "Individuals who provide reliable information based on their media experience", "Professional journalists employed by news agencies", "Celebrities who promote commercial products"],
                correct: 1
            },
            {
                question: "Who are Opinion Leaders?",
                choices: ["People who interpret and pass on information to others", "People who ignore the news", "People who write for entertainment magazines", "People who post memes online"],
                correct: 0
            },
            {
                question: "The Two-Step Flow Communication Model was developed by ________.",
                choices: ["Claude Shannon and Warren Weaver", "Wilbur Schramm", "Paul Lazarsfeld, Bernard Berelson, and Hazel Gaudet", "David Berlo"],
                correct: 2
            },
            {
                question: "People without professional journalism training who report events online are called ________.",
                choices: ["Anchors", "Broadcasters", "Citizen Journalists", "Columnists"],
                correct: 2
            },
            {
                question: "Social Journalism is best defined as ________.",
                choices: ["Writing personal blogs", "Using social media to distribute journalistic content widely", "Publishing print newspapers", "Broadcasting through radio"],
                correct: 1
            },
            {
                question: "The process of obtaining ideas or content from a large online group is called ________.",
                choices: ["Collaboration", "Campaigning", "Outsourcing", "Crowdsourcing"],
                correct: 3
            },
            {
                question: "People in Media are ________.",
                choices: ["Ordinary citizens who express personal opinions", "Students of journalism", "Professionals who share information based on expertise or firsthand experience", "Political leaders using media for influence"],
                correct: 2
            },
            {
                question: "Which of the following is not a type of journalist by medium?",
                choices: ["Broadcast Journalist", "Multimedia Journalist", "Print Journalist", "Political Journalist"],
                correct: 3
            },
            {
                question: "What does the case of Nestor Punzalan teach us about social media use?",
                choices: ["Trust viral posts immediately", "Believe everything you see online", "Always verify information before sharing", "Avoid using the internet completely"],
                correct: 2
            },
            {
                question: "What is ubiquitous learning?",
                choices: ["Learning that happens anytime and anywhere using technology", "Learning that occurs only inside the classroom", "Learning that depends on printed materials", "Learning that requires face-to-face interaction only"],
                correct: 0
            },
            {
                question: "Which of the following is a characteristic of ubiquitous learning?",
                choices: ["Temporariness", "Permanency", "Exclusivity", "Limitation"],
                correct: 1
            },
            {
                question: "What does immediacy mean in ubiquitous learning?",
                choices: ["Learning materials can be accessed only in school", "Students can immediately access materials wherever they are", "Teachers control when lessons can be viewed", "Internet access is not required"],
                correct: 1
            },
            {
                question: "What is the main purpose of interactivity in ubiquitous learning?",
                choices: ["To promote collaboration among teachers and students online", "To restrict access to online materials", "To limit communication to formal settings", "To encourage isolation in studying"],
                correct: 0
            },
            {
                question: "What does MOOC stand for?",
                choices: ["Massive Open Online Course", "Media Oriented Online Class", "Modern Online Open Curriculum", "Mobile Oriented Online Course"],
                correct: 0
            }
        ];

        let currentQuestionIndex = 0;
        let score = 0;
        let timeLeft = 300; // 5 minutes in seconds
        let timer;
        let shuffledQuestions = [];
        let studentInfo = {};
        let answered = false;

        function shuffleArray(array) {
            const shuffled = [...array];
            for (let i = shuffled.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [shuffled[i], shuffled[j]] = [shuffled[j], shuffled[i]];
            }
            return shuffled;
        }

        function shuffleChoices(question) {
            const correctAnswer = question.choices[question.correct];
            const shuffledChoices = shuffleArray(question.choices);
            const newCorrectIndex = shuffledChoices.indexOf(correctAnswer);
            
            return {
                ...question,
                choices: shuffledChoices,
                correct: newCorrectIndex
            };
        }

        function initializeQuiz() {
            shuffledQuestions = shuffleArray(questions).map(shuffleChoices);
            currentQuestionIndex = 0;
            score = 0;
            timeLeft = 300;
            answered = false;
            
            document.getElementById('currentScore').textContent = score;
            updateProgress();
            displayQuestion();
            startTimer();
        }

        function startTimer() {
            timer = setInterval(() => {
                timeLeft--;
                updateTimerDisplay();
                
                if (timeLeft <= 0) {
                    clearInterval(timer);
                    endQuiz();
                }
            }, 1000);
        }

        function updateTimerDisplay() {
            const minutes = Math.floor(timeLeft / 60);
            const seconds = timeLeft % 60;
            document.getElementById('timer').textContent = `⏰ ${minutes}:${seconds.toString().padStart(2, '0')}`;
        }

        function updateProgress() {
            const progress = (currentQuestionIndex / shuffledQuestions.length) * 100;
            document.getElementById('progressFill').style.width = `${progress}%`;
        }

        function displayQuestion() {
            if (currentQuestionIndex >= shuffledQuestions.length) {
                endQuiz();
                return;
            }

            const question = shuffledQuestions[currentQuestionIndex];
            answered = false;
            
            document.getElementById('questionNumber').textContent = `Question ${currentQuestionIndex + 1} of 15`;
            document.getElementById('questionText').textContent = question.question;
            
            const choicesContainer = document.getElementById('choices');
            choicesContainer.innerHTML = '';
            
            question.choices.forEach((choice, index) => {
                const choiceElement = document.createElement('div');
                choiceElement.className = 'choice';
                choiceElement.textContent = choice;
                choiceElement.onclick = () => selectAnswer(index);
                choicesContainer.appendChild(choiceElement);
            });
            
            document.getElementById('feedback').classList.add('hidden');
            document.getElementById('nextBtn').classList.add('hidden');
            document.getElementById('bonusTime').classList.add('hidden');
        }

        function selectAnswer(selectedIndex) {
            if (answered) return;
            
            answered = true;
            const question = shuffledQuestions[currentQuestionIndex];
            const choices = document.querySelectorAll('.choice');
            const feedbackElement = document.getElementById('feedback');
            
            choices[selectedIndex].classList.add('selected');
            
            if (selectedIndex === question.correct) {
                choices[selectedIndex].classList.add('correct');
                score++;
                timeLeft += 5; // Add 5 seconds bonus
                
                // Show bonus time animation
                const bonusElement = document.getElementById('bonusTime');
                bonusElement.classList.remove('hidden');
                setTimeout(() => {
                    bonusElement.classList.add('hidden');
                }, 2000);
                
                feedbackElement.textContent = '✅ Correct! Great job!';
                feedbackElement.className = 'feedback correct';
                
                document.getElementById('currentScore').textContent = score;
            } else {
                choices[selectedIndex].classList.add('incorrect');
                
                feedbackElement.textContent = `❌ Incorrect. Try again next time!`;
                feedbackElement.className = 'feedback incorrect';
            }
            
            feedbackElement.classList.remove('hidden');
            
            // Disable all choices
            choices.forEach(choice => {
                choice.style.pointerEvents = 'none';
            });
            
            setTimeout(() => {
                document.getElementById('nextBtn').classList.remove('hidden');
            }, 1500);
        }

        function nextQuestion() {
            currentQuestionIndex++;
            updateProgress();
            displayQuestion();
        }

        function endQuiz() {
            clearInterval(timer);
            
            document.getElementById('quizInterface').classList.add('hidden');
            document.getElementById('results').classList.remove('hidden');
            
            const percentage = (score / shuffledQuestions.length) * 100;
            const passed = percentage >= 80;
            
            const scoreElement = document.getElementById('finalScore');
            scoreElement.textContent = `${score}/${shuffledQuestions.length} (${percentage.toFixed(1)}%)`;
            scoreElement.className = `score ${passed ? 'pass' : 'fail'}`;
            
            const messageElement = document.getElementById('resultMessage');
            const actionsElement = document.getElementById('resultActions');
            
            if (passed) {
                messageElement.innerHTML = `
                    <h3 style="color: #00b894;">🎉 Congratulations! You Passed!</h3>
                    <p>Excellent work! You've demonstrated a solid understanding of GAMABA and Filipino traditional arts.</p>
                `;
                
                actionsElement.innerHTML = `
                    <button class="btn btn-success" onclick="sendResultsToTeacher()" style="margin-right: 15px;">
                        📧 Send Results to Teacher
                    </button>
                    <button class="btn btn-primary" onclick="retakeQuiz()">
                        🔄 Retake Quiz
                    </button>
                `;
            } else {
                messageElement.innerHTML = `
                    <h3 style="color: #e17055;">📚 Keep Learning!</h3>
                    <p>You need 80% to pass. Don't give up - practice makes perfect!</p>
                `;
                
                actionsElement.innerHTML = `
                    <a href="https://www.youtube.com/@princeyahwetv" target="_blank" rel="noopener noreferrer" class="btn btn-youtube" style="margin-right: 15px;">
                        📺 Subscribe for Study Help
                    </a>
                    <button class="btn btn-primary" onclick="retakeQuiz()">
                        🔄 Retake Quiz
                    </button>
                `;
            }
        }

        function sendResultsToTeacher() {
            const subject = encodeURIComponent(`Quiz Results - ${studentInfo.name}`);
            const body = encodeURIComponent(`
Dear Teacher,

Student Information:
- Name: ${studentInfo.name}
- Grade: ${studentInfo.grade}
- Section: ${studentInfo.section}

Quiz Results:
- Score: ${score}/${shuffledQuestions.length}
- Percentage: ${((score / shuffledQuestions.length) * 100).toFixed(1)}%
- Status: PASSED ✅

The student has successfully completed the GAMABA: National Living Treasures Quiz with a passing grade.

Best regards,
Quiz System
            `);
            
            window.open(`mailto:joel.rodriguez@deped.gov.ph?subject=${subject}&body=${body}`, '_blank');
        }

        function retakeQuiz() {
            document.getElementById('results').classList.add('hidden');
            document.getElementById('dashboard').classList.remove('hidden');
            document.getElementById('quizInterface').classList.remove('hidden');
            
            initializeQuiz();
        }

        // Event Listeners
        document.getElementById('studentForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            studentInfo = {
                name: document.getElementById('studentName').value,
                grade: document.getElementById('studentGrade').value,
                section: document.getElementById('studentSection').value
            };
            
            document.getElementById('displayName').textContent = studentInfo.name;
            document.getElementById('displayGrade').textContent = studentInfo.grade;
            document.getElementById('displaySection').textContent = studentInfo.section;
            
            document.getElementById('registration').classList.add('hidden');
            document.getElementById('dashboard').classList.remove('hidden');
            document.getElementById('quizInterface').classList.remove('hidden');
            
            initializeQuiz();
        });

        document.getElementById('nextBtn').addEventListener('click', nextQuestion);
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'990fad2682a3febc',t:'MTc2MDg3MDYyNi4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
