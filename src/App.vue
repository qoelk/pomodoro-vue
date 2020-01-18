<template>
  <div id="app">
  <notification></notification>
    <div class="main-container">
      <timer :timeLeft="this.timeLeft"></timer>
      <div class="buttons-wrap">
        <button @click="start">Start</button>
        <button @click="pause">Pause</button>
        <button @click="stop">Stop</button>
        <button @click="reset">Reset</button>
      </div>
    </div>
  </div>
</template>

<script>
import Timer from './components/Timer.vue'
import Notification from './components/Notification.vue'

export default {
  name: 'app',
  components: {
    Timer,
    Notification
  },
  data() {
    return {
      isClockRunning: false,
      timeLeft: 1500,
      workDuration: 25,
      shortBreakDuration: 5,
      longBreakDuration: 30,
      timer: null
    }

  },
  methods: {
    start() {
      if (!this.timer) {
        this.timer = setInterval(() => {
          if(this.timeLeft>0){
            this.timeLeft--;
          } else this.stop();
        }, 1000)
      }
    },
    pause() {
      if(this.timer) {
        clearInterval(this.timer);
        this.timer = null;
      }
    },
    stop() {
      this.pause();
      this.timeLeft = 0;
    },
    reset() {
      this.pause();
      this.timeLeft = 1500;
    }
  }
}
</script>

<style>

#app {
  background-color: black;
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: monospace;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;

}
</style>
