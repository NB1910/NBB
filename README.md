<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gra z Wskazówkami</title>
    <style>
        body {
            font-family: Montserrat, sans-serif;
            margin: 0;
            padding: 0;
            background-color: hsl(0, 0%, 96%);
            color: #FF8D42;
            text-align: center;
        }
        .container {
            max-width: 600px;
            margin: 20px auto;
            padding: 20px;
            background-color: #e4e3e2;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        h1 {
            color: #FF8D42;
        }
        .instructions, .question, .answer {
            margin-bottom: 30px;
        }
        .answer input {
            padding: 10px;
            font-size: 16px;
            width: 100%;
            margin: 10px 0;
        }
        .answer button {
            padding: 10px 20px;
            background-color: #FF8D42;
            color: white;
            border: none;
            cursor: pointer;
            font-size: 16px;
        }
        .answer button:hover {
            background-color: #e67335;
        }
        .hint {
            font-size: 18px;
            color: #28a745;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Test</h1>
        <div id="startScreen">
            <p>Rozpocznij ekscytującą przygodę, w której będziesz musiał odnaleźć ukryte pytania i podać poprawne odpowiedzi, aby zdobyć kolejne wskazówki prowadzące Cię aż do mety!</p>
            <button onclick="startGame()">Start</button>
        </div>
        <div id="game" class="game" style="display: none;">
            <div id="question1" class="question">
                <p id="hint1" class="hint">Wskazówka do odnalezienia pierwszego pytania: Choć w tym miejscu brak zasięgu Wi-Fi, strzegący tej areny Cerber kieruje swój surowy wzrok na największą skarbnicę wiedzy, która istniała przed erą Internetu. </p>
                <p>Jaka jest odpowiedź na pytanie?</p>
                <div class="answer">
                    <input type="text" id="answer1" placeholder="Twoja odpowiedź">
                    <button onclick="checkAnswer('answer1', 'NB', 'hint1')">Sprawdź odpowiedź</button>
                </div>
            </div>
            <div id="question2" class="question" style="display: none;">
                <p id="hint2" class="hint">Brawo! To stare drzewo przy placu zabaw.</p>
                <p>Wskaż miejsce przy którym jest kolejna wskazówka?</p>
                <div class="answer">
                    <input type="text" id="answer2" placeholder="Twoja odpowiedź">
                    <button onclick="checkAnswer('answer2', 'drzewo', 'hint2')">Sprawdź odpowiedź</button>
                </div>
            </div>
            <div id="question3" class="question" style="display: none;">
                <p id="hint3" class="hint">Doskonała odpowiedź! Przejdź na skrzyżowanie w pobliżu rynku.</p>
                <p>Gdzie znajduje się kolejna wskazówka?</p>
                <div class="answer">
                    <input type="text" id="answer3" placeholder="Twoja odpowiedź">
                    <button onclick="checkAnswer('answer3', 'skrzyżowanie', 'hint3')">Sprawdź odpowiedź</button>
                </div>
            </div>
            <div id="question4" class="question" style="display: none;">
                <p id="hint4" class="hint">Świetnie! Wskazówka znajduje się przy pomniku w centrum miasta.</p>
                <p>Gdzie znajdziesz kolejną wskazówkę?</p>
                <div class="answer">
                    <input type="text" id="answer4" placeholder="Twoja odpowiedź">
                    <button onclick="checkAnswer('answer4', 'pomnik', 'hint4')">Sprawdź odpowiedź</button>
                </div>
            </div>
            <div id="question5" class="question" style="display: none;">
                <p id="hint5" class="hint">Gratulacje! Finał odbywa się w sklepie na rogu ulicy.</p>
                <p>Gdzie znajduje się finał?</p>
                <div class="answer">
                    <input type="text" id="answer5" placeholder="Twoja odpowiedź">
                    <button onclick="checkAnswer('answer5', 'sklep', 'hint5')">Sprawdź odpowiedź</button>
                </div>
            </div>
        </div>
    </div>
    <script>
        function startGame() {
            document.getElementById("startScreen").style.display = "none";
            document.getElementById("game").style.display = "block";
        }

        function checkAnswer(inputId, correctAnswer, hintId) {
            var answer = document.getElementById(inputId).value.toLowerCase();
            if (answer === correctAnswer.toLowerCase()) {
                document.getElementById(hintId).style.display = "block";
                showNextQuestion(inputId);
            } else {
                alert("Niestety, odpowiedź jest błędna. Spróbuj ponownie!");
            }
        }

        function showNextQuestion(currentInputId) {
            var currentQuestion = document.getElementById("question" + getQuestionNumber(currentInputId));
            var nextQuestion = document.getElementById("question" + (getQuestionNumber(currentInputId) + 1));
            if (nextQuestion) {
                currentQuestion.style.display = "none";
                nextQuestion.style.display = "block";
            }
        }

        function getQuestionNumber(inputId) {
            return parseInt(inputId.replace('answer', ''));
        }
    </script>
</body>
</html>
