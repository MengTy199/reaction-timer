<template>
  <div class="result">
    <h1>Reaction time:  {{ score }} ms</h1>
  <p class="rank">{{ rank }}</p>
  </div>
</template>

<script>
export default {
  name: "ResultsApp",
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 250) {
      this.rank = "Mengty Fingers";
    } else if (this.score < 400) {
      this.rank = "Rapid Reflexes";
    } else {
      this.rank = "Snail pace ...";
    }
  },
};
</script>

<style>
.result{
  margin-top: 20px;
}
.result > h1{
  font-size: 1.2rem;
  margin-bottom: 10px;
  font-weight: bold;
}.result > p{
  font-size: 1.2rem;
  text-align: center;
}
</style>
