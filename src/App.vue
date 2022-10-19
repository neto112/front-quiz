<template>
  <div>
    <Quiz @quiz-completed="handleQuizCompleted" :key="quizKey" />
    <Modal
      v-show="showModal"
      v-bind:quizScore="quizScore"
      @reload="updateQuiz"
      @close="showModal = false"
    />
  </div>
</template>

<script>
import Quiz from "@/components/Quiz.vue";
import Modal from "@/components/Modal.vue";

export default {
  name: "App",
  components: {
    Modal,
    Quiz,
  },
  data() {
    return {
      quizKey: 0,
      showModal: false,
      quizScore: {
        allQuestions: 0,
        answeredQuestions: 0,
        correctlyAnsweredQuestions: 0,
      },
    };
  },
  methods: {
    handleQuizCompleted(score) {
      this.quizScore = score;
      this.showModal = true;
    },
    updateQuiz() {
      this.showModal = false;
      this.quizKey++;
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
}
</style>
