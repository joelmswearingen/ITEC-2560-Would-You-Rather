<template>
  <div id="app">
    <h1>Would you rather...</h1>  

    <WouldYouRatherQuestion 
      v-for="question in questions"
      v-bind:key="question.id"
      v-bind:question="question"
      v-on:answer-changed="answerChanged"
    ></WouldYouRatherQuestion>

    <h2>You Would Rather...</h2>  
    <ul>
        <li 
          v-for="choice in choices"
          v-bind:key="choice.id"
        >{{ choice }}</li>
    </ul>
  </div>
</template>

<script>
import WouldYouRatherQuestion from './components/WouldYouRatherQuestion.vue'

export default {
  name: 'App',
  components: {
    WouldYouRatherQuestion
  },
  data() {
    return {
      questions: [
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
      choices: [],
    }
  },
  methods: {
    answerChanged(choice) {
        let index = choice.id
        this.choices[index] = choice.choice
        this.$set(this.choices, index, choice.choice)
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
