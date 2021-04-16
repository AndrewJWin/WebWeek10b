<template>
  <div class="wyr">
    <h2>Would you rather?</h2>
    <h3>{{question.wyrQuestion}}</h3>
    
    <input v-bind:id="question1" type="radio" 
      v-bind:value="question.wyrAnswer1"
      v-model="choice"
      v-on:change="choiceMade">
    <label for="question1">{{ question.wyrAnswer1 }}</label>
    
    <input v-bind:id="question2" type="radio"
      v-bind:value="question.wyrAnswer2"
      v-model="choice"
      v-on:change="choiceMade">
    <label for="question2">{{ question.wyrAnswer2 }}</label>
  </div>
</template>

<script>
export default {
  name: 'WouldYouRather',
  props: {
    question: Object
  },
  data() {
    return {
      choice:String
    }
  },
  methods: {
    choiceMade() {
      this.$emit("answer-changed", this.question.id, this.choice)
    }
  }
}
</script>

<style scoped>
h3 {
  margin: 20px 0 0;
}

.wyr {
  color: black;
  background: linear-gradient(silver, gray);
  border: 2px black solid;
  margin: 10px;
}

input {
  margin: 10px;
  font-weight: bold;
  color: black;
}
</style>
