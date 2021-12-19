<template>
  <h1>Reaction Time {{ score }} ms</h1>
  <p class="rank">{{rank}}</p>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 250) {
      return (this.rank = "good");
    } else if (this.score < 400) {
      return "not bad";
    } else {
      return (this.rank = "noobs");
    }
  },
};
</script>

<style></style>
