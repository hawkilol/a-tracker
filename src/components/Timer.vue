<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <Cronometer :timeInSeconds="timeInSeconds" />
    <button class="button" @click="play" :disabled="cronometerRunning">
      <span class="icon">
        <i class="fas fa-play"></i>
      </span>
      <span>play</span>
    </button>
    <button class="button" @click="stop" :disabled="!cronometerRunning">
      <span class="icon">
        <i class="fas fa-stop"></i>
      </span>
      <span>stop</span>
    </button>
  </div>
</template>

<script lang="ts">

import { defineComponent } from "vue";
import Cronometer from './Cronometer.vue'
export default defineComponent({
  name: "Timer",
  emits: ['TimerEnded'],
  components: {
    Cronometer
  },
  data () {
    return {
      timeInSeconds: 0,
      cronometer: 0,
      cronometerRunning: false
    }
  },
  methods: {
        play() {
            // começar a contagem
            // 1 seg = 1000 ms
            this.cronometerRunning = true
            this.cronometer = setInterval(() => {
                this.timeInSeconds += 1
            }, 1000)
        },

        
        stop() {
            this.cronometerRunning = false
            clearInterval(this.cronometer)
            this.$emit('TimerEnded', this.timeInSeconds)
            this.timeInSeconds = 0
        }
    }
});
</script>

