<template>
  <div>

    <h2>{{ question.question }}</h2>

    <input type="radio" v-model="choice" v-bind:value="answer1" v-on:click="userAnswerSelected(choice)">
    <label>{{ question.answer1 }}</label>
    <input type="radio" v-model="choice" v-bind:value="answer2" v-on:click="userAnswerSelected(choice)">
    <label>{{ question.answer2 }}</label>

  </div>
</template>

<script>
export default {
  name: 'WouldYouRatherQuestion',
  data() {
    return {
      choice: ''
    }
  }, 
  props: {
    id: Number,
    question: Object,
    answer1: String,
    answer2: String,
    answers: Array,
  },
  methods: {
    userAnswerSelected(choice) {
      this.$emit('choice-selected', choice)
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

</style>
