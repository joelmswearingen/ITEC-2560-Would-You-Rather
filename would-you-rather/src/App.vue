<template>
  <div id="app">
    <h1>Would you rather...</h1>  

    <WouldYouRatherQuestion 
      v-for="question in questions"
      v-bind:key="question.id"
      v-bind:question="question"
      v-bind:choice="choice"
      v-on:choice-selected="userAnswerSelected"
    ></WouldYouRatherQuestion>

    <h2>You Would Rather...</h2>  
    <div>
        {{ userSelectionMessage }}            
    </div>
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
          answer1: 'reverse centaur',
          answer2: 'reverse mermaid/merman',
        },
        {
          id: 1,
          question: '...be raised by monkeys or by wolves?',
          answer1: 'monkeys',
          answer2: 'wolves',          
        },
        {
          id: 2,
          question: '...have hooves for feet or webbed fingers?',
          answer1: 'hooves for feet',
          answer2: 'webbed fingers',          
        },
      ],
      answers: [],
      userSelectionMessage: '',
    }
  },
  method: {
    userAnswerSelected(choice) {
      this.answers.push(choice)
    },

  },
}
</script>


<style>

</style>
