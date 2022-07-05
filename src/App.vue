<template>
  <h1 class="title">Quiz App</h1>
  <Question
    :question="currentQuestion"
    :answerd="answerd"
    @handleNextQuestion="handleNextQuestion"
    @handleAnswerSelected="handleAnswerSelected"
    @reset="reset"
    :finshed="finshed"
    :score="score"
    :length="questions.length"
  />
</template>

<script>
import Question from "./components/Question.vue";
export default {
  name: "App",
  components: {
    Question,
  },
  data() {
    return {
      currQuestion: 0,
      answerd: "",
      finshed: false,
      event: null,
      score: 0,
      questions: [
        {
          question:
            "What do you call a computer on a network that requests files from another computer?",
          answer: 0,
          options: ["A client", "A host", "A router", "A web server"],
        },
        {
          question:
            "Hardware devices that are not part of the main computer system and are often added later to the system.",
          answer: 0,
          options: ["Peripheral", "Clip art", "Highlight", "Execute"],
        },
        {
          question:
            "The main computer that stores the files that can be sent to computers that are networked together is:",
          answer: 3,
          options: ["Clip art", "Mother board", "Peripheral", "File server"],
        },
        {
          question: "How can you catch a computer virus?",
          answer: 2,
          options: [
            "Sending e-mail messages",
            "Using a laptop during the winter",
            "Opening e-mail attachments",
            "Shopping on-line",
          ],
        },
        {
          question: "Google (www.google.com) is a:",
          answer: 0,
          options: [
            "Search Engine",
            "Number in Math",
            "Directory of images",
            "Chat service on the web",
          ],
        },
        {
          question: "Which is not an Internet protocol?",
          answer: 2,
          options: ["HTTP", "FTP", "STP", "IP"],
        },
        {
          question: "Which of the following is not a valid domain name?",
          answer: 0,
          options: [
            "www.yahoo.com",
            "www.yahoo.co.uk",
            "www.com.yahoo",
            "www.yahoo.co.in",
          ],
        },
        {
          question: "AOL stands for:",
          answer: 3,
          options: [
            "Arranged Outer Line",
            "America Over LAN",
            "Audio Over LAN",
            "America On-line",
          ],
        },
        {
          question: "Another name for a computer chip is:",
          answer: 1,
          options: ["Execute", "Micro chip", "Microprocessor", "Select"],
        },
        {
          question: "'www' stands for:",
          answer: 0,
          options: ["World Wide Web", "World Wide Wares", "World Wide Wait", "World Wide War"],
        },
      ],
    };
  },
  methods: {
    handleNextQuestion() {
      if (this.answerd == this.questions[this.currQuestion].answer) {
        this.score++;
      }
      console.log("score", this.score);
      this.currQuestion++;
      this.answerd = "";
      this.event.target.checked = false;
      if (this.currQuestion == this.questions.length) {
        this.finshed = true;
      }
    },
    handleAnswerSelected(event) {
      this.answerd = event.target.value;
      this.event = event;
    },

    reset() {
      this.answerd = "";
      this.finshed = false;
      this.currQuestion = 0;
      this.score = 0;
    },
  },
  computed: {
    currentQuestion() {
      return this.questions.find((ques, index) => index === this.currQuestion);
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #f1faee;
  margin-top: 60px;
}
body {
  background-color: #457b9d;
}
.title {
  margin-bottom: 3rem;
}
</style>
