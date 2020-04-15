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
        > {{ choice.choice }} </li>
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
        this.choices.push(choice)       
        // how to replace existing object where key exists?
        // add sort?
    },
  },
}
</script>


<style>

</style>
