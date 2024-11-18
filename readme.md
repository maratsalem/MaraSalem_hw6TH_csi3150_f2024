# Quiz App Demo Tutorial

## Lesson Outcome

- (fill)

### Pre-requisites

- This project will be using html, javascript, and css.
- If you want to test your App development as you progress, make sure you have a live server available for use.
- Recommended development software: Visual Studio Code.
  -Recommended development extensions for Visual Studio Code: Live Server, JavaScript (ES6) code snippets, HTML CSS Support, HTML Snippets

### Tutorial Steps

- Background: (mention something about building with javascript as a functional backend/storing data within it and being able to gather data and utilize it).

#### Step 1: Project directory setup

1. Create a project folder in your desired project path. Then, create a new project in Visual Studio Code with the project folder you have created.

2. Inside the folder, create an index.html file, and two new folders: JS and CSS. Inside the CSS folder, create a style.css file. Inside the JS folder, create questions.js and quizApp.js files.
   -Note: This step can be done manually through the UI, or through bash. The choice is up to you.

- Your project directory should look like this:
  Project Folder
  CSS
  style.css
  JS
  questions.js
  quizApp.js
  index.html

#### Step 2: Inserting quiz questions into questions.js

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

#### Step 3: Build HTML UI

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

2. Create file in root directory called ./store.js and add the following code:

```javascript
import { configureStore } from "@reduxjs/toolkit";

import quesReducer from "./slices/questionSlice";

const store = configureStore({
  reducer: {
    questionData: questionReducer,
  },
});

export default store;
```

3. Create a sub-folder in the root directory called slices, and inside it create a file called questionSlice.js, and add the following code:

```javascript
import { createSlice } from "@reduxjs/toolkit";

//initial state - all the checkbox options that we give to the user. One state for each option
/**
 * Q1: What is/are your preferred programming languages
 *   a. Python b. Java c. JavaScript d. C/C++
 *
 * Q2. Where would you apply for a job?
 *   a. Facebook b. Apple c. Netflix d. Google
 */
const initialState = {
  languageOptionPython: false,
  languageOptionJava: false,
  languageOptionJavascript: false,
  languageOptionC: false,
  companyOptionFacebook: false,
  companyOptionApple: false,
  companyOptionNetflix: false,
  companyOptionGoogle: false,
};

// create data slice
export const questionSlice = createSlice({
  name: "questionData",
  initialState,
  reducers: {
    setLanguageOptionPython: (state, action) => {
      state.languageOptionPython = action.payload;
    },
    setLanguageOptionJava: (state, action) => {
      state.languageOptionJava = action.payload;
    },
    setLanguageOptionJavascript: (state, action) => {
      state.languageOptionJavascript = action.payload;
    },
    setLanguageOptionC: (state, action) => {
      state.languageOptionC = action.payload;
    },
    setCompanyOptionFacebook: (state, action) => {
      state.companyOptionFacebook = action.payload;
    },
    setCompanyOptionApple: (state, action) => {
      state.companyOptionApple = action.payload;
    },
    setCompanyOptionNetflix: (state, action) => {
      state.companyOptionNetflix = action.payload;
    },
    setCompanyOptionGoogle: (state, action) => {
      state.companyOptionGoogle = action.payload;
    },
  },
});

// export reducers
export const {
  setLanguageOptionPython,
  setLanguageOptionJava,
  setLanguageOptionJavascript,
  setLanguageOptionC,
  setCompanyOptionFacebook,
  setCompanyOptionApple,
  setCompanyOptionNetflix,
  setCompanyOptionGoogle,
} = questionSlice.actions;

// create and export selectors
export const selectLanguageOptionPython = (state) =>
  state.questionData.languageOptionPython;

export const selectLanguageOptionJava = (state) =>
  state.questionData.languageOptionJava;

export const selectLanguageOptionJavascript = (state) =>
  state.questionData.languageOptionJavascript;

export const selectLanguageOptionC = (state) =>
  state.questionData.languageOptionC;

export const selectCompanyOptionFacebook = (state) =>
  state.questionData.companyOptionFacebook;

export const selectCompanyOptionApple = (state) =>
  state.questionData.companyOptionApple;

export const selectCompanyOptionNetflix = (state) =>
  state.questionData.companyOptionNetflix;

export const selectCompanyOptionGoogle = (state) =>
  state.questionData.companyOptionGoogle;

export default questionSlice.reducer;
```

4. In App.js wrap your NavigationContainer component in the Provider component after importing it and add the prop store and connect it with your data store file after importing it to App.js

```javascript
//import this
import store from "./store";

// add this inside return()
<Provider store={store}>// rest of the app</Provider>;
```

#### Step4: Add Checkbox component

1. Open file ./components/QuestionCard.js

BUG NOTE: The previous package discussed for Checkboxes is not compatible with Expo.

2. Use the following package for checkboxes: https://docs.expo.dev/versions/latest/sdk/checkbox/

install it by:

```
npx expo install expo-checkbox
```

3. remove the boilerplate code and add the following code:

```javascript
import { Button, SafeAreaView, StyleSheet, Text, View } from "react-native";
import React from "react";

//import for Checkbox component. Make sure package is installed~
// DOES NOT WORK ~
// import CheckBox from "@react-native-community/checkbox";

// different checkbox package
import Checkbox from "expo-checkbox";

//redux hook import to call dispatch to execute the reducers
import { useDispatch } from "react-redux";

// import all the reducers from data slice
import {
  setLanguageOptionPython,
  setLanguageOptionJava,
  setLanguageOptionJavascript,
  setLanguageOptionC,
  setCompanyOptionFacebook,
  setCompanyOptionApple,
  setCompanyOptionNetflix,
  setCompanyOptionGoogle,
} from "../slices/questionSlice";

//imports for selectors
import { useSelector } from "react-redux";
import {
  selectLanguageOptionPython,
  selectLanguageOptionJava,
  selectLanguageOptionJavascript,
  selectLanguageOptionC,
  selectCompanyOptionFacebook,
  selectCompanyOptionApple,
  selectCompanyOptionNetflix,
  selectCompanyOptionGoogle,
} from "../slices/questionSlice";

//import for navigation
import { useNavigation } from "@react-navigation/native";

const QuestionCard = () => {
  const dispatch = useDispatch();
  const languageOptionPython = useSelector(selectLanguageOptionPython);
  const languageOptionJava = useSelector(selectLanguageOptionJava);
  const languageOptionJavascript = useSelector(selectLanguageOptionJavascript);
  const languageOptionC = useSelector(selectLanguageOptionC);
  const companyOptionFacebook = useSelector(selectCompanyOptionFacebook);
  const companyOptionApple = useSelector(selectCompanyOptionApple);
  const companyOptionNetflix = useSelector(selectCompanyOptionNetflix);
  const companyOptionGoogle = useSelector(selectCompanyOptionGoogle);

  const navigation = useNavigation();
  return (
    <SafeAreaView>
      <View style={styles.questionWrapper}>
        <Text style={{ fontSize: 22, paddingBottom: 15 }}>
          Welcome, Jon Snow!
        </Text>

        <View>
          <Text style={styles.questionText}>
            Choose preferred programming languages:
          </Text>

          <View style={styles.questionOptions}>
            <Checkbox
              disabled={false}
              value={languageOptionPython}
              onValueChange={(newValue) => {
                dispatch(setLanguageOptionPython(newValue));
              }}
            />
            <Text>Python</Text>

            <View style={styles.questionOptions}>
              <Checkbox
                disabled={false}
                value={languageOptionJava}
                onValueChange={(newValue) => {
                  dispatch(setLanguageOptionJava(newValue));
                }}
              />
              <Text>Java</Text>
            </View>

            <View style={styles.questionOptions}>
              <Checkbox
                disabled={false}
                value={languageOptionJavascript}
                onValueChange={(newValue) => {
                  dispatch(setLanguageOptionJavascript(newValue));
                }}
              />
              <Text>JavaScript</Text>
            </View>

            <View style={styles.questionOptions}>
              <Checkbox
                disabled={false}
                value={languageOptionC}
                onValueChange={(newValue) => {
                  dispatch(setLanguageOptionC(newValue));
                }}
              />
              <Text>C/C++</Text>
            </View>
          </View>
        </View>

        <View>
          <Text style={styles.questionText}>
            Choose companies to apply for job:
          </Text>

          <View style={styles.questionOptions}>
            <Checkbox
              disabled={false}
              value={companyOptionFacebook}
              onValueChange={(newValue) => {
                dispatch(setCompanyOptionFacebook(newValue));
              }}
            />
            <Text>Facebook</Text>
          </View>

          <View style={styles.questionOptions}>
            <Checkbox
              disabled={false}
              value={companyOptionApple}
              onValueChange={(newValue) => {
                dispatch(setCompanyOptionApple(newValue));
              }}
            />
            <Text>Apple</Text>
          </View>

          <View style={styles.questionOptions}>
            <Checkbox
              disabled={false}
              value={companyOptionNetflix}
              onValueChange={(newValue) => {
                dispatch(setCompanyOptionNetflix(newValue));
              }}
            />
            <Text>Netflix</Text>
          </View>

          <View style={styles.questionOptions}>
            <Checkbox
              disabled={false}
              value={companyOptionGoogle}
              onValueChange={(newValue) => {
                dispatch(setCompanyOptionGoogle(newValue));
              }}
            />
            <Text>Google</Text>
          </View>
        </View>

        <Button
          title="Submit"
          color="#f194ff"
          onPress={() => navigation.navigate("AnswerScreen")}
        />
      </View>
    </SafeAreaView>
  );
};

export default QuestionCard;

const styles = StyleSheet.create({
  questionWrapper: {
    display: "flex",
  },
  questionText: {
    fontSize: 18,
    padding: 10,
  },
  questionOptions: {
    // flex: 1,
    flexDirection: "row",
    gap: 10,
    // alignItems: "center",
    // justifyContent: "center",
    paddingLeft: 8,
  },
});
```

#### Step 5: render selected option on the UI

1. Open AnswerCard.js file in ./components and replace existing code with the following code:

```javascript
import {
  FlatList,
  StyleSheet,
  Text,
  TouchableOpacity,
  View,
} from "react-native";
import React from "react";

//imports for selectors
import { useSelector } from "react-redux";
import {
  selectLanguageOptionPython,
  selectLanguageOptionJava,
  selectLanguageOptionJavascript,
  selectLanguageOptionC,
  selectCompanyOptionFacebook,
  selectCompanyOptionApple,
  selectCompanyOptionNetflix,
  selectCompanyOptionGoogle,
} from "../slices/questionSlice";

const AnswerCard = () => {
  const languageOptionPython = useSelector(selectLanguageOptionPython);
  const languageOptionJava = useSelector(selectLanguageOptionJava);
  const languageOptionJavascript = useSelector(selectLanguageOptionJavascript);
  const languageOptionC = useSelector(selectLanguageOptionC);
  const companyOptionFacebook = useSelector(selectCompanyOptionFacebook);
  const companyOptionApple = useSelector(selectCompanyOptionApple);
  const companyOptionNetflix = useSelector(selectCompanyOptionNetflix);
  const companyOptionGoogle = useSelector(selectCompanyOptionGoogle);
  return (
    <View>
      <Text>Jon Sno, Your Preferred Options are: </Text>

      <View>
        <Text>Selected Programming Languages </Text>
        {languageOptionPython && <Text>Python</Text>}
        {languageOptionJava && <Text>Java</Text>}
        {languageOptionJavascript && <Text>JavaScript</Text>}
        {languageOptionC && <Text>C/C++</Text>}
      </View>

      <View>
        <Text>Selected Companies</Text>
        {companyOptionFacebook && <Text>Facebook</Text>}
        {companyOptionApple && <Text>Apple</Text>}
        {companyOptionNetflix && <Text>Netflix</Text>}
        {companyOptionGoogle && <Text>Google</Text>}
      </View>
    </View>
  );
};

export default AnswerCard;

const styles = StyleSheet.create({});
```

###### Self Exercises

- Add styling
- Use Flatlist component for conditional rendering of list items
- Use TouchableOpacity instead of Checkboxes to acheive the same functionality (Hint: See Uber Clone readme section for ride type selection option.)
