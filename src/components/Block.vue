<template>
  <div class="block" v-if="showBlock" @click="stopTimer">click me</div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      reactionTime: 0,
    };
  },
  mounted() {
    // console.log("mounted()");
    // console.log(this.delay);
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer()
      console.log(this.delay);
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("end",this.reactionTime)
      console.log(this.reactionTime)
    },
  },
  updated() {
    console.log("updated()");
  },
  unmounted() {
    console.log("unmounted()");
  },
};
</script>

<style scoped>
.block {
  background: crimson;
  color: #fff;
  text-align: center;
  width: 600px;
  height: 200px;
  display: flex;
  justify-content: center;
  margin: auto;
  padding-top: 100px;
}
</style>
