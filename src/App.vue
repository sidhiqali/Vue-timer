<template>
  <h1>My Reaction Timer</h1>
  <button
    @click="start"
    :disabled="isPlaying"
  >
    Play
  </button>
  <Block
    v-if="isPlaying"
    :delay="delay"
  />
</template>

<script>
import Block from "./components/block.vue";
export default {
  name: "App",
  components: {
    Block,
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      console.log(this.delay);
    },
  },
};
</script>

<style>
#app {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  margin-top: 70px;
  font-family: "Times New Roman", Times, serif;
  font-weight: 300;
  color: darkgreen;
}
button {
  width: 70px;
  height: 30px;
  background-color: rgb(19, 121, 200);
  border: 1px solid green;
  color: white;
}
button:disabled {
 opacity: 0.4;
}
</style>
