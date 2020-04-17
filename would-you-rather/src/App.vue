<template>
  <div id="app">
    <h1>Would you rather...</h1>  
    <!-- Displays inputs from the WouldYouRatherQuestions.vue component and loops over and passing the questions in the array below to the child component which will handle them
    This also receives information emitted from the child -->
    <WouldYouRatherQuestion 
      v-for="question in questions"
      v-bind:key="question.id"
      v-bind:question="question"
      v-on:answer-changed="answerChanged"
    ></WouldYouRatherQuestion>


    <h2>You Would Rather...</h2>  
    <ul>
    <!-- Loops over and displays user selections committed to Choices array by method answerChanged -->          
        <li 
          v-for="choice in choices"
          v-bind:key="choice.id"
        >{{ choice }}</li>
    </ul>
  </div>
</template>

<script>
// imports WouldYouRatherQuestion component for use
import WouldYouRatherQuestion from './components/WouldYouRatherQuestion.vue'

export default {
  name: 'App',
  components: { // identifies child components
    WouldYouRatherQuestion
  },
  data() {
    return {
      questions: [ // array of questions, each question being an object with and id, question, answer1, and answer2
        {
          id: 0,
          question: '...be a reverse centaur or a reverse mermaid/merman?',
          answer1: 'Be a reverse centaur',
          answer2: 'Be a reverse mermaid/merman',
        },
        {
          id: 1,
          question: '...be raised by monkeys or by wolves?',
          answer1: 'Be raised by monkeys',
          answer2: 'Be raised by wolves',        
        },
        {
          id: 2,
          question: '...have hooves for feet or webbed fingers?',
          answer1: 'Have hooves for feet',
          answer2: 'Have webbed fingers', 
        },
      ],
      choices: [], // empty array for choices to be added
    }
  },
  methods: {
    answerChanged(choice) {  // emitted from child (see WouldYouRatherQuestion element v-on for connection) every time the user selects or changes an answer
        let index = choice.id // identifes choice/id key/property from object passed from child and assigns a variable
        this.choices[index] = choice.choice // adds the choice/choice key/property to the index in the choices array defined in the line above
        this.$set(this.choices, index, choice.choice) // forces vue to recognize that the property in the array has changed, allowing it to become reactive and update
        }
    },
}
</script>


<style>
body {
  background-color: aliceblue;
  border: 0;
  margin: 15px;
  padding: 10px;
}

h1, h2 {
  font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
  font-size: 45px;
  font-style: italic;
  margin: 0;
  padding: 10px;
  text-align: center;
}

h2 {
  font-size: 35px;
  margin-top: 20px;
}

input {
  margin-left: 35px;
}

label {
  margin-left: 5px;
}

ul {
  margin: auto;
  padding: 0;
  text-align: center;
  width: 50%;
}

li {
  color: darkslateblue;
  display: block;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  font-size: large;
  font-style: italic;
  width: auto;
}
</style>
