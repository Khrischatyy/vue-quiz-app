<template>
  <div class="questions-ctr">
    <div class="progress">
      <div class="bar" :style="{ width: `${(questionAnswered / questions.length) * 100}%`}"></div>
      <div class="status">{{questionAnswered }} out of {{questions.length}} questions answered</div>
    </div>

    <transition-group name="fade">
      <div v-show="qi === questionAnswered" v-for="(question, qi) in questions" :key="question.q" class="single-question">
        <div class="question">{{question.q}}</div>
        <div class="answers">
          <div @click.prevent="selectAnswer(answer.is_correct)"
               class="answer"
               v-for="answer in question.answers"
               :key="answer.text">{{answer.text}}</div>
        </div>
    </div>
    </transition-group>
  </div>
</template>

<script>
export default {
  name: "Questions",
  props: {
    questions: Array,
    questionAnswered: Number,
  },
  emits: ['increment-answered-question'],
  methods: {
    selectAnswer(isCorrect) {
      this.$emit('increment-answered-question', isCorrect)
    }
  }
}
</script>

<style scoped>

</style>