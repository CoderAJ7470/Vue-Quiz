<template>
  <div class="questionBlock">
    <h4>Q{{ questionCount }}: {{ currentQuestion.value }}</h4>

    <div>
      <ol class="answerChoices">
        <li
          v-for="(answer, index) in answers" v-bind:key="index"
          v-on:click="checkSelectedAnswer(answer.isCorrect, index)"
          :class="addClassesUponSelection(answer.isCorrect, index)">
          {{ answer.id }}. {{ answer.text }}
          </li>
      </ol>
    </div>

    <button
      :disabled="notAnswered"
      @click="next(); checkEndOfQuiz();">
        Next
    </button>
    <Score :score="score" :totalQuestions="totalQuestions"/>
  </div>
</template>

<script>
import Score from './Score.vue';

export default {
  name: 'QABlock',
  components: {
    Score
  },
  props: {
    currentQuestion: Object,
    next: Function,
    questionCount: Number,
    totalQuestions: Number
  },
  data() {
    return {
      score: 0,
      selectedItemIndex: null,
      notAnswered: true,
      answerCorrect: false
    }
  },
  computed: {
    answers() {
      let answers = [...this.currentQuestion.choices]; // creating a copy of an array and assigning it to a variable
      return answers;
    }
  },
  watch: {
    currentQuestion: {
      immediate: true,
      handler() {
        this.selectedItemIndex = null,
        this.notAnswered = true;
      }
    }
  },
  methods: {
    checkSelectedAnswer(correctAnswer, index) {
      this.notAnswered = false;
      this.selectedItemIndex = index;

      if(correctAnswer) {
        this.score += 1;
        this.answerCorrect = true
      }
    },
    addClassesUponSelection(correctAnswer, index) {
      // let cssClass = '';
      let classArray = [];
      let answerTypeClass, disabledClass = '';

      // console.log(index);

      if(!this.notAnswered) {
        disabledClass = 'disabled';
        classArray.push(disabledClass);
      }

      if(!this.notAnswered && correctAnswer) {
        answerTypeClass = 'correctAnswer';
      }
      else if(this.selectedItemIndex === index && !this.notAnswered && !correctAnswer) {
        answerTypeClass = 'incorrectAnswer';
      }

      classArray.push(answerTypeClass);

      // return cssClass;
      return classArray;
    },
    checkEndOfQuiz() {
      if(this.questionCount === this.totalQuestions) {
        this.score = 0;
      }
    }
  }
}
</script>