<template>
  <div class="scoreKeeper">
    Your Score: {{ score }} out of {{ totalQuestions }}
  </div>
</template>

<script>
export default {
  props: {
    score: Number,
    totalQuestions: Number
  }
}
</script>