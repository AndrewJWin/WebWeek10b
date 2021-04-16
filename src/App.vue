<template>
  <div id="app">
    <h1>Would you rather...</h1>
    <would-you-rather v-for="question in wyrQuestions"
      v-bind:key="question.id"
      v-bind:question=question
      v-on:answer-changed="answerChanged">
    </would-you-rather>

    <div id="answers">
      <h1>You would rather...</h1>
      <ul v-if="userSelection.length > 0" >
        <li v-for="choice in choicesAvailable" v-bind:key="choice">{{choice}}</li>
      </ul>
      <p v-else>Not answer it seems? Please make a selection above.</p>
    </div>
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
      wyrQuestions: [
        {
          id: 0,
          wyrQuestion: "Would you rather be able to speak any language but not be able to read in any of them or read any language but not be able to speak any of them?",
          wyrAnswer1: "Speak any language",
          wyrAnswer2: "Read every language",
        },
        {
          id: 1,
          wyrQuestion: "Would you rather be able to find anything that was lost or every time you touched someone they would be unable to lie?",
          wyrAnswer1: "Find everything",
          wyrAnswer2: "Touch for truth",
        },
        {
          id: 2,
          wyrQuestion: "Would you rather be able to remember everything in every book you read or remember every conversation you have?",
          wyrAnswer1: "Remember the book",
          wyrAnswer2: "Remember the speech",
        }
      ],
      userSelection: []
    }
  },
  methods: {
    answerChanged(id, choice) {
      this.userSelection[id] = choice;
    }
  },
  computed: {
    choicesAvailable() {
      // Avoid displaying not-yet-chosen choices
      return this.userSelection.filter( choice => choice )
    }
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300&display=swap');
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#answers {
  font-family: Roboto, sans-serif;
  font-size: 15pt;
}

li {
  text-align: inherit;
  list-style-type: disc;
  list-style-position: inside;
  font-size: 1.2em;
}

p {
  font-family: Roboto, sans-serif;
  font-size: 20pt;
}
</style>
