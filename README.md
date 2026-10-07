<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>English Placement Test</title>

    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            min-height: 100vh;
            background: #f4f1eb;
            color: #252525;
            font-family: Arial, Helvetica, sans-serif;

            display: flex;
            justify-content: center;
            align-items: center;

            padding: 30px;
        }

        .test-container {
            width: 100%;
            max-width: 760px;
        }

        /* TOP */

        .top {
            display: flex;
            justify-content: space-between;
            align-items: center;

            margin-bottom: 28px;
        }

        .brand {
            font-size: 12px;
            letter-spacing: 2.5px;
            font-weight: 600;
            text-transform: uppercase;
        }

        .question-number {
            font-size: 13px;
            color: #777;
        }

        /* CARD */

        .card {
            background: #fffdf9;
            border-radius: 24px;
            padding: 55px;

            box-shadow:
                0 20px 60px rgba(0, 0, 0, 0.07);

            min-height: 570px;

            display: flex;
            flex-direction: column;
        }

        .eyebrow {
            font-size: 11px;
            letter-spacing: 2px;
            text-transform: uppercase;

            color: #7a8068;

            margin-bottom: 18px;
        }

        h1 {
            font-family: Georgia, "Times New Roman", serif;
            font-size: clamp(36px, 6vw, 58px);
            line-height: 1.05;
            font-weight: 400;

            margin-bottom: 18px;
        }

        .subtitle {
            color: #777;
            font-size: 15px;
            line-height: 1.6;

            max-width: 480px;
            margin-bottom: 40px;
        }

        /* PROGRESS */

        .progress-wrapper {
            margin-bottom: 38px;
        }

        .progress-info {
            display: flex;
            justify-content: space-between;

            font-size: 11px;
            color: #888;

            margin-bottom: 9px;
        }

        .progress {
            width: 100%;
            height: 3px;

            background: #e4e0d8;
            border-radius: 10px;

            overflow: hidden;
        }

        .progress-bar {
            height: 100%;
            width: 33.333%;

            background: #7a8068;

            transition: width 0.35s ease;
        }

        /* QUESTION */

        .question {
            font-family: Georgia, "Times New Roman", serif;
            font-size: 27px;
            line-height: 1.35;

            margin-bottom: 28px;
        }

        /* OPTIONS */

        .options {
            display: grid;
            gap: 11px;
        }

        .option {
            width: 100%;

            background: transparent;
            border: 1px solid #dedbd3;

            border-radius: 12px;

            padding: 17px 19px;

            text-align: left;

            font-size: 15px;
            color: #333;

            cursor: pointer;

            transition:
                background 0.2s ease,
                border-color 0.2s ease,
                transform 0.2s ease;
        }

        .option:hover {
            border-color: #9da38a;
            transform: translateY(-1px);
        }

        .option.selected {
            background: #eef0e8;
            border-color: #7a8068;
        }

        .option.correct {
            background: #e7eee3;
            border-color: #728568;
        }

        .option.incorrect {
            background: #f3e7e4;
            border-color: #b77c72;
        }

        /* BOTTOM */

        .bottom {
            margin-top: auto;
            padding-top: 35px;

            display: flex;
            justify-content: flex-end;
        }

        .next-button {
            border: none;
            background: #252525;
            color: white;

            border-radius: 50px;

            padding: 14px 27px;

            font-size: 13px;
            font-weight: 600;

            cursor: pointer;

            transition:
                transform 0.2s ease,
                opacity 0.2s ease;
        }

        .next-button:hover {
            transform: translateY(-2px);
        }

        .next-button:disabled {
            opacity: 0.3;
            cursor: default;
            transform: none;
        }

        /* RESULT */

        .result {
            display: none;
            text-align: center;

            align-items: center;
            justify-content: center;
        }

        .result-number {
            font-family: Georgia, "Times New Roman", serif;
            font-size: 90px;
            line-height: 1;

            margin: 25px 0;
        }

        .result-text {
            color: #777;
            font-size: 15px;
            line-height: 1.6;

            max-width: 430px;
            margin-bottom: 35px;
        }

        .restart-button {
            border: 1px solid #252525;
            background: transparent;
            color: #252525;

            border-radius: 50px;

            padding: 14px 27px;

            font-size: 13px;
            font-weight: 600;

            cursor: pointer;
        }

        /* MOBILE */

        @media (max-width: 600px) {

            body {
                padding: 16px;
            }

            .card {
                padding: 32px 25px;
                min-height: 600px;
                border-radius: 20px;
            }

            h1 {
                font-size: 42px;
            }

            .question {
                font-size: 23px;
            }

            .top {
                margin-bottom: 18px;
            }
        }
    </style>
</head>

<body>

<div class="test-container">

    <!-- TOP -->

    <div class="top">
        <div class="brand">
            English Placement
        </div>

        <div class="question-number" id="questionNumber">
            01 / 03
        </div>
    </div>


    <!-- TEST CARD -->

    <div class="card" id="testCard">

        <div class="eyebrow">
            Diagnostic test
        </div>

        <div class="progress-wrapper">

            <div class="progress-info">
                <span>Progress</span>
                <span id="progressText">1 of 3</span>
            </div>

            <div class="progress">
                <div class="progress-bar" id="progressBar"></div>
            </div>

        </div>


        <div class="question" id="question">
            I ___ English for three years.
        </div>


        <div class="options" id="options">

            <button class="option" onclick="selectAnswer(0)">
                study
            </button>

            <button class="option" onclick="selectAnswer(1)">
                am studying
            </button>

            <button class="option" onclick="selectAnswer(2)">
                have been studying
            </button>

            <button class="option" onclick="selectAnswer(3)">
                studied
            </button>

        </div>


        <div class="bottom">

            <button
                class="next-button"
                id="nextButton"
                onclick="nextQuestion()"
                disabled
            >
                Next →
            </button>

        </div>

    </div>


    <!-- RESULT -->

    <div class="card result" id="resultCard">

        <div class="eyebrow">
            Test complete
        </div>

        <h1>
            Well done.
        </h1>

        <div class="result-number" id="resultNumber">
            2 / 3
        </div>

        <div class="result-text" id="resultText">
            Your answers give us a first idea of your current English level.
        </div>

        <button
            class="restart-button"
            onclick="restartTest()"
        >
            Try again
        </button>

    </div>

</div>


<script>

    const questions = [

        {
            question: "I ___ English for three years.",
            options: [
                "study",
                "am studying",
                "have been studying",
                "studied"
            ],
            correct: 2
        },

        {
            question: "If I ___ more time, I would learn another language.",
            options: [
                "have",
                "had",
                "will have",
                "would have"
            ],
            correct: 1
        },

        {
            question: "She suggested ___ the meeting until Monday.",
            options: [
                "to postpone",
                "postpone",
                "postponing",
                "postponed"
            ],
            correct: 2
        }

    ];


    let currentQuestion = 0;
    let score = 0;
    let selectedAnswer = null;


    function loadQuestion() {

        selectedAnswer = null;

        const question = questions[currentQuestion];

        document.getElementById("question").textContent =
            question.question;

        document.getElementById("questionNumber").textContent =
            String(currentQuestion + 1).padStart(2, "0")
            + " / "
            + String(questions.length).padStart(2, "0");

        document.getElementById("progressText").textContent =
            `${currentQuestion + 1} of ${questions.length}`;

        document.getElementById("progressBar").style.width =
            `${((currentQuestion + 1) / questions.length) * 100}%`;


        const optionsContainer =
            document.getElementById("options");

        optionsContainer.innerHTML = "";


        question.options.forEach((option, index) => {

            const button = document.createElement("button");

            button.className = "option";

            button.textContent = option;

            button.onclick = function () {
                selectAnswer(index);
            };

            optionsContainer.appendChild(button);

        });


        document.getElementById("nextButton").disabled = true;

        document.getElementById("nextButton").textContent =
            currentQuestion === questions.length - 1
                ? "Finish →"
                : "Next →";
    }


    function selectAnswer(index) {

        selectedAnswer = index;

        const buttons =
            document.querySelectorAll(".option");

        buttons.forEach((button, i) => {

            button.classList.remove("selected");

            if (i === index) {
                button.classList.add("selected");
            }

        });


        document.getElementById("nextButton").disabled = false;
    }


    function nextQuestion() {

        if (selectedAnswer === null) {
            return;
        }


        if (
            selectedAnswer ===
            questions[currentQuestion].correct
        ) {
            score++;
        }


        currentQuestion++;


        if (currentQuestion < questions.length) {

            loadQuestion();

        } else {

            showResult();

        }

    }


    function showResult() {

        document.getElementById("testCard").style.display =
            "none";

        document.getElementById("resultCard").style.display =
            "flex";


        document.getElementById("resultNumber").textContent =
            `${score} / ${questions.length}`;


        let message;


        if (score === 3) {

            message =
                "Excellent start. Your answers show a strong command of these structures.";

        } else if (score === 2) {

            message =
                "Good job. You already have a solid foundation, with a few areas worth checking.";

        } else {

            message =
                "Thank you. This gives us a useful starting point for looking at your English.";

        }


        document.getElementById("resultText").textContent =
            message;
    }


    function restartTest() {

        currentQuestion = 0;

        score = 0;

        document.getElementById("resultCard").style.display =
            "none";

        document.getElementById("testCard").style.display =
            "flex";

        loadQuestion();
    }


    loadQuestion();

</script>

</body>
</html>
