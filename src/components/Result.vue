<template>
  <div class="result">
      <div class="title">{{result.title}}</div>
      <div class="desc">{{result.desc}}</div>
  </div>
</template>

<script>
export default {
  name: "Result",
  props: {
    results: Array,
    totalCorrect: Number,
  },
  computed: {
    result() {
      let index = 0;

      this.results.forEach((r, i) => {
        if (r.min <= this.totalCorrect && r.max >= this.totalCorrect) {
          index = i;
        }
      })

      return this.results[index];
    }
  }
}
</script>

<style scoped>

</style>