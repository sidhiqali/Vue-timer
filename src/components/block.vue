<template>
  <div
    v-if="showModel"
    class="block"
    @click="stopTimer"
  >
    <div v-if="showResult">
      <div>Your Result is:</div>
      <div class="result">{{ reactionTime }} ms</div>
      <button class="button" @click="tryAgain">Try Again</button>
    </div>
    <div v-else>Click Me</div>
  </div>
</template>

<script>
export default {
  name: "Block",
  props: ["delay"],
  data() {
    return {
      showModel: false,
      timer: null,
      reactionTime: 0,
      showResult: false,
    };
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      console.log(this.reactionTime);
      this.showResult = true;
    },
    tryAgain() {
      this.$emit("playEnd");
    },
  },
  mounted() {
    console.log("mounted");
    setTimeout(() => {
      this.showModel = true;
      console.log("done");
      this.startTimer();
    }, this.delay);
  },
  updated() {
    console.log("updated");
  },
};
</script>

<style>
.block {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 30px;
  width: 350px;
  height: 200px;
  background-color: rgb(12, 123, 101);
  color: white;
  border-radius: 20px;
}
.result{
  font-size: xxx-large;
  color: goldenrod;
}
.button {
  margin-top: 20px;
  border-radius: 30px;
  width: 100px;
  height: 30px;
  background-color: lightseagreen;
  border: 2px solid rgb(98, 171, 147);
}
</style>
