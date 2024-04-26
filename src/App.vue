<template>
  <div class="container">
    <div class="item">
      <h1>Mengty Reaction Timer</h1>
      <button class="btn" @click="start" :disabled="isPlaying">Play</button>
      <BlockModal v-if="isPlaying" :delay="delay" @end="endGame" />
      <Results v-if="showResults" :score="score" />
    </div>
  </div>
</template>

<script>
import BlockModal from "./components/BlockModal.vue";
import Results from "./components/Results.vue";

export default {
  name: "App",
  components: { BlockModal, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResults = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
    },
  },
};
</script>

<style>
*,body{
  margin: 0;
  padding: 0;
}
.container{
  margin: 0 auto;
  padding: 0;
  display: flex;
  justify-content: center;
  height: 100vh;
  width: 100%;
  align-items: center;
  background-color: #ffffff;
}
.container > .item{
  display: flex;
  align-items: center;
  flex-direction: column;
  justify-content: center;
  border: 2px solid green;
  padding: 100px;
  transform: rotate(3deg);
  transition: all ease-in-out 0.4s;
  width: auto;
  
}
@media only screen and (max-width: 600px) {
  .container{
    width: 80%;
  }
  .item {
    width: 60%;
  }
  .item > h1{
    font-size: 1.2rem;
  }
}
.container > .item:hover{
  transform: rotate(-3deg)

}
.btn {
  margin-top: 30px;
  background-color: aquamarine;
  border: 2px solid aquamarine;
  padding: 10px 30px;
  font-size: 1.3rem;
  cursor: pointer;
  border-radius: 10px;
}
.btn:hover {
  background-color: #ffff;
}
</style>
