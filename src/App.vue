<template>
<div id="app">
  <h1>Would you rather...</h1>
  <would-you-rather 
    v-bind:question="wyrQuestion"
    v-bind:answer1="wyrAnswer1"
    v-bind:answer2="wyrAnswer2"
    v-on:answer-changed="answerChanged">
  </would-you-rather>

  <p>{{userSelectionMessage}}</p>

</div>
</template>

<script>
import WouldYouRather from './components/WouldYouRather.vue'

export default {
  name: 'App',
  components: {
    WouldYouRather
  },
  data() {
    return {
      wyrQuestion: "Would you rather be able to speak any language but not be able to read in any of them or read any language but not be able to speak any of them?",
      wyrAnswer1: "Speak any language",
      wyrAnswer2: "Read every language",
      userSelectionMessage: ""
    }
  },
  methods: {
    answerChanged(choice) {
      this.userSelectionMessage = `Thanks, you chose to ${choice}`
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300&display=swap');
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

p {
  font-family: Roboto, sans-serif;
  font-size: 20pt;
}
</style>
