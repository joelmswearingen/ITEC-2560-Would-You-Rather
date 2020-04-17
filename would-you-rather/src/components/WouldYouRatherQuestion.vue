<template>
  <div>
    <h2>Would you rather...</h2>

    <!-- Using the props (question object) from the parent and the loop definied in the WouldYouRatherQuestion element on the parent,
    this template is set up to look at each object interation in the questions array to display the question and answers for each question. -->
    <h3>{{ question.question }}</h3>

    <!-- v-bind:id in the input and v-bind:for in the label allow either the quesiton or the radio button to be click for the selection to be made -->
    <!-- v-model ensures that the radio buttons are treated like a unit, allowing only one to be selected -->
    <!-- v-bind:value connects the each questions answer to the radio button -->
    <!-- v-on:change invokes the "checked(choice)" method in the script below-->
    <input type="radio" v-bind:id="question.answer1" v-model="choice" v-bind:value="question.answer1" v-on:change="checked(choice)">
    <label v-bind:for="question.answer1">{{ question.answer1 }}</label>
    <input type="radio" v-bind:id="question.answer2" v-model="choice" v-bind:value="question.answer2" v-on:change="checked(choice)">
    <label v-bind:for="question.answer2">{{ question.answer2 }}</label>
  </div>
</template>

<script>
export default {
  name: 'WouldYouRatherQuestion', // identifes the name of the child element to connect to the parent
  data() {
    return {
      choice: '' // empty string to add the current choice for each question
    }
  }, 
  props: {
    question: Object,  // allows the parent to share data/property elements with the child, in this instance it shares the object "question" from the questions array in the parent
  },
  methods: {
    checked(choice) {  // method groups the user choice and the associated question id into an object and sets it to a variable
      let answer = { id: this.question.id, choice: this.choice }
      this.$emit('answer-changed', answer)  // /this emits our variable with the user selections to the parent
    }
  },
}
</script>

<!-- "scoped" attribute added to style to limit CSS to this component only -->
<style scoped>
h2 {
  color: darkslateblue;  
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  font-size: x-large;
  font-style: italic;
  margin: 0;
  padding: 20px 25px 10px 5px;
  text-align: left;
}

h3 {
  font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
  margin: 0;
  padding: 5px 15px;
}

/* Styling for input/labels are held at the parent level so that they can be more widly used in case of expansion */
</style>
