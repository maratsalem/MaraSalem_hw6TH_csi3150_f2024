# Quiz App Demo Tutorial

## Quiz App

The purpose of this application is to provide a web quiz application that tests the user’s knowledge from a select topic.

## Functional Features

- The application must be able to display questions on a browser, and react to the user selecting an answer.
- The application must be able to determine the correct answer and display it after the user has submitted their answer.
- The application must be able to time the user's response time towards each quiz question.
- The quiz timer should be an optional choice for the user.

## Pre-requisites

- This project will be built using html, javascript, and css.
- If you want to test your App development as you progress, make sure you have a live server available for use.
- Recommended development software: Visual Studio Code.
  -Recommended development extensions for Visual Studio Code: Live Server, JavaScript (ES6) code snippets, HTML CSS Support

## Tutorial Steps

### Step 1: Project directory setup

1. Create a project folder in your desired project path. Then, create a new project in Visual Studio Code with the project folder you have created.

2. Inside the folder, create an index.html file, and two new folders: JS and CSS. Inside the CSS folder, create a style.css file. Inside the JS folder, create questions.js and quizApp.js files.

Note: This step can be done manually through the UI, or through bash. The choice is up to you.

- Your project directory should look like this:

```
  Project Folder
    CSS
        style.css
    JS
        questions.js
        quizApp.js
  index.html
```

### Step 2: Inserting quiz questions into questions.js

- The 'questions.js' file functions as our 'backend' in this project. This javascript file will hold our quiz questions and answers, which we can then import to our quizApp.js for further use.

- Inside of this JS file, we create an array 'questions' that contains objects with the following members: question number, questions, options, and answers. The questions provided involve coding languages, but feel free to modify the questions, answers, and options to your liking.

1. Inside of the ./JS/questions.js fil insert the following code:

```
// creating an array of objects
let questions = [
  {
    numb: 1,
    question: "What does HTML stand for?",
    answer: "Hyper Text Markup Language",
    options: [
      "Hyper Text Preprocessor",
      "Hyper Text Markup Language",
      "Hyper Text Multiple Language",
      "Hyper Tool Multi Language",
    ],
  },
  {
    numb: 2,
    question: "What does CSS stand for?",
    answer: "Cascading Style Sheet",
    options: [
      "Common Style Sheet",
      "Colorful Style Sheet",
      "Computer Style Sheet",
      "Cascading Style Sheet",
    ],
  },
  {
    numb: 3,
    question: "What does PHP stand for?",
    answer: "Hypertext Preprocessor",
    options: [
      "Hypertext Preprocessor",
      "Hypertext Programming",
      "Hypertext Preprogramming",
      "Hometext Preprocessor",
    ],
  },
  {
    numb: 4,
    question: "What does SQL stand for?",
    answer: "Structured Query Language",
    options: [
      "Stylish Question Language",
      "Stylesheet Query Language",
      "Statement Question Language",
      "Structured Query Language",
    ],
  },
  {
    numb: 5,
    question: "What does XML stand for?",
    answer: "eXtensible Markup Language",
    options: [
      "eXtensible Markup Language",
      "eXecutable Multiple Language",
      "eXTra Multi-Program Language",
      "eXamine Multiple Language",
    ],
  },
  // Duplicate the object declaration and initialization above for more questions
];

```

### Step 3: Build HTML UI

1. Inside index.html, include the following code:

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quiz App Demo</title>

    <!-- CSS FILE -->
    <link rel="stylesheet" href="./css/style.css">
    <!-- This is my personal font awesome kit code. you will have to add your own after you register with email-->
    <script src="https://kit.fontawesome.com/4a4f4b55b0.js" crossorigin="anonymous"></script>
    
     <!-- Add questions list -->
    <script src="./js/questions.js" defer></script>

    <!-- Main logic of the app -->
    <script src="./js/quizApp.js" defer></script>
</head>
<body>
    <!-- Quiz START Button -->
    <div class="start_btn"><button>Start Quiz</button></div>

    <!-- Instruction box wrapper -->
    <div class="info_box">
        <div class="info-title"><span>Some Rules of this Quiz</span></div>
        <div class="info-list">
            <div class="info">1. You will have only <span>15 seconds</span> per each question.</div>
            <div class="info">2. Once you select your answer, it can't be undone.</div>
            <div class="info">3. You can't select any option once time goes off.</div>
            <div class="info">4. You can't exit from the Quiz while you're playing.</div>
            <div class="info">5. You'll get points on the basis of your correct answers.</div>
        </div>
        <div class="buttons">
            <button class="quit">Exit Quiz</button>
            <button class="restart">Continue</button>
        </div>
    </div>

    <!-- Quiz Box -->
    <div class="quiz_box">
        <header>
            <div class="title">Demo Quiz App in JavaScript</div>
            <div class="timer">
                <div class="time_left_txt">Time Left</div>
                <div class="timer_sec">15</div>
            </div>
            <div class="time_line"></div>
        </header>
        <section>
            <div class="que_text">
                <!-- Insert questions from ./js/questions.js -->
            </div>
            <div class="option_list">
                <!-- Insert options to questions from ./js/questions.js -->
            </div>
        </section>

        <!-- footer of Quiz Box -->
        <footer>
            <div class="total_que">
                <!-- insert Question Count Number dynamically from JavaScript App logic -->
            </div>
            <button class="next_btn">Next Que</button>
        </footer>
    </div>

    <!-- Result Box -->
    <div class="result_box">
        <div class="icon">
            <i class="fas fa-crown"></i>
        </div>
        <div class="complete_text">You've completed the Quiz!</div>
        <div class="score_text">
            <!-- insert dynamic user score as Result from JavaScript -->
        </div>
        <div class="buttons">
            <button class="restart">Replay Quiz</button>
            <button class="quit">Quit Quiz</button>
        </div>
    </div>

</body>
</html>
</html>

```
