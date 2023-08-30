<template>
  <div class="main">
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
      @playEnd="endPlaying"
    />
  </div>
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
    endPlaying() {
      this.isPlaying = false;
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
  color: rgb(62, 120, 62);
}
.main {
  padding: 20px;
  border-radius: 20px;
  border: 2px solid rgb(209, 206, 206);
}
button {
  width: 70px;
  height: 30px;
  background-color: rgba(107, 111, 115, 0.806);
  border: 1px solid green;
  color: white;
  border-radius: 10px;
}
button:hover {
  cursor: pointer;
}
button:disabled {
  opacity: 0.4;
}
</style>
