<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <transition name="modal">
    <div class="modal-task">
      <div class="modal-wrapper">
        <div class="modal-container">
          <div class="modal-header">
            <h2>Congratulations</h2>
            <h3>You've completed your Quiz!</h3>
          </div>
          <div class="modal-body">
            You answered
            {{
              Math.floor(
                quizScore.correctlyAnsweredQuestions / quizScore.allQuestions
              ) * 100
            }}
            % correctly! Answered {{ quizScore.correctlyAnsweredQuestions }} out
            of {{ quizScore.allQuestions }} questions.
          </div>
          <div class="modal-footer">
            <button @click="$emit('reload')">Play again</button>
            <button @click="$emit('close')">Close</button>
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  props: {
    quizScore: Object,
  },
};
</script>

<style scoped>
.modal-task {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: table;
}

.modal-wrapper {
  display: table-cell;
  vertical-align: middle;
}

.modal-container {
  width: 90vw;
  max-width: 650px;
  margin: auto;
  padding: 2rem;
  background-color: #fff;
  border-radius: 6px;
}

.modal-header {
  text-align: center;
}

.modal-header h2,
h3 {
  color: rgb(0, 178, 72);
}

.modal-body {
  padding: 2rem 0;
  text-align: center;
}

.modal-footer {
  display: flex;
  justify-content: space-between;
}

button {
  padding: 1rem 2rem;
  background: linear-gradient(
    210deg,
    rgba(187, 0, 47, 0.8),
    rgba(245, 0, 87, 0.6)
  );
  border-radius: 7px;
  border: none;
  font-size: 1rem;
  font-weight: 600;
  color: darkblue;
}
</style>