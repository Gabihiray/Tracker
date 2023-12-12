<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <StopWatcher :timeSeconds="timeSeconds"/>
        <Button @click="start" icon="fas fa-play" text="play" :disabled="stopWatcherRunning"/>
        <Button @click="stop" icon="fas fa-stop" text="stop" :disabled="!stopWatcherRunning"/>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import StopWatcher from './StopWatcher.vue'
import Button from './Button.vue'
export default defineComponent({
    name: 'Timer-card',
    emits: ['timerFinished'],
    components: {
      StopWatcher,
      Button
    },
    data (){
      return {
        timeSeconds: 0,
        stopWatcher: 0,
        stopWatcherRunning: false
      }
    },
    //Creating methods to give actions to buttons
    methods: {
      // start score
      // 1 Second = 1000 ms
      start () {
        this.stopWatcherRunning = true
        this.stopWatcher = setInterval(() => {
          this.timeSeconds += 1
        }, 1000)
      },
      stop () {
        this.stopWatcherRunning = false
        clearInterval(this.stopWatcher)
        this.$emit('timerFinished', this.timeSeconds)
        this.timeSeconds = 0
      }
    }
})
</script>