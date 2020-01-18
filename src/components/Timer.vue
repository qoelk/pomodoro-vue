<template>
  <span>{{this.counter}}</span>
</template>

<script>
export default {
  name: 'Timer',
  props: {
    timeLeft: Number
  },
  data() {
    return {

    }
  },
  computed: {
    counter() {
      let minutes = parseInt(this.timeLeft/60);
      let seconds = this.timeLeft%60;
      seconds = seconds < 10 ? `0${seconds}` : seconds;
      return minutes + ':' + seconds;
    }
  },
  methods: {

  },
  mounted() {
  
}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  span {
    font-size: 12vw;
  }
</style>
