<template>
  <div class="box form">
    <div class="columns">
      <div
        class="column is-8"
        role="form"
        aria-label="Formulário para a criação de uma nova tarefa"
      >
        <input
          type="text"
          class="input"
          placeholder="Qual tarefa você deseja iniciar?"
          v-model="description"
        />
      </div>
      <div class="column">
        <Timer @timerFinished="finishedTask"/>
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue'
import Timer from './Timer.vue'
export default defineComponent({
    name: 'Form-card',
    emits: ['savingTask'],
    components: {
      Timer,
    },
    data () {
    return{
      description: '',
    }
    },
    methods: {
      finishedTask (timeElapsed: number) : void {
        this.$emit('savingTask', {
          durationSeconds: timeElapsed,
          description: this.description,
        })
        this.description = ''
      }
    }
})
</script>

<style>
.form {
  color: var(--text-primary);
  background-color: var(--bg-primary);
}
.input {
  color: var(--text-primary);
  background-color: var(--bg-card);
}
.input::placeholder {
  color: var(--text-primary)
}
</style>