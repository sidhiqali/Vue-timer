<template>
  <div
    v-if="showModel"
    class="block"
  >
    <div>Click Me</div>
  </div>
</template>

<script>
export default {
  name: "Block",
  props: ["delay"],
  data() {
    return {
      showModel: false,
    };
  },
  mounted() {
    console.log("mounted");
    setTimeout(() => {
      this.showModel = true;
      console.log('done')
    }, this.delay);
  },
  updated(){
    console.log("updated");
  }
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
</style>
