<template>
  <section class="question-container" v-if="!finshed">
    <h2 class="question-title">{{ question.question }}</h2>
    <ul class="question-options-container">
      <li
        v-for="(option, index) in question.options"
        :key="index"
        class="question-option"
      >
        <input
          type="radio"
          :id="index"
          :value="index"
          name="question"
          class="question-option-input"
          @change="$emit('handleAnswerSelected', $event)"
        />
        <label :for="index" class="question-option-title">{{ option }}</label>
      </li>
    </ul>
    <button
      :class="answerd ? 'button' : 'disabledButton'"
      :disabled="answerd ? false : true"
      @click="$emit('handleNextQuestion')"
    >
      SELECT AN OPTION
    </button>
  </section>
  <section v-else>
    <h2>Score {{ score }} from {{ length }}</h2>
    <button class="returnButton" @click="$emit('reset')">Return</button>
  </section>
  <!-- <h2>{{ question }}</h2> -->
</template>

<script>
export default {
  name: "QuestionT",
  props: {
    question: Object,
    answerd: String,
    finshed: Boolean,
    score: Number,
    length: Number,
  },
  data() {
    return {
      test: "",
    };
  },
  emits: ["handleNextQuestion", "handleAnswerSelected", "reset"],
};
</script>


<style>
.question-container {
  margin: auto;
  text-align: start;
  width: 75%;
  border: 1px solid #fff;
  padding: 2rem 2rem 2rem 4rem;
}

.question-options-container {
  list-style-type: none;
  text-align: start;
}

.question-title {
  margin-bottom: 1.5rem;
}

.question-option {
  background-color: #f1faee;
  color: #457b9d;
  font-size: 1.3rem;
  font-weight: bold;
  margin-bottom: 0.5rem;
  padding: 1rem;
}

.question-option-title {
  cursor: pointer;
}

.question-option-input {
  margin-right: 10px;
}

.button {
  font-size: 1.5rem;
  color: #fff;
  padding: 1rem;
  border: 0;
  border: 1px solid #f1faee;
  background-color: transparent;
  margin-top: 1rem;
  cursor: pointer;
}
.disabledButton {
  font-size: 1.5rem;
  color: #fff;
  padding: 1rem;
  border: 0;
  border: 1px solid #f1faee;
  background-color: transparent;
  margin-top: 1rem;
  opacity: 0.5;
  /* cursor: pointer; */
}

.returnButton {
  font-size: 2rem;
  color: #fff;
  padding: 1rem;
  border: 0;
  border: 1px solid #f1faee;
  background-color: transparent;
  margin-top: 1rem;
  cursor: pointer;
}

.returnButton:hover {
  background-color: #f1faee;
  color: #457b9d;
}
</style>
