<template>
<main class="columns is-gapless is-multiline" :class="{ 'mode-dark': modeDarkActive }">
  <div class="column is-one-quarter">
    <BarraLateral @themeChange="exchangeTheme"/>
  </div>
  <div class="column is-three-quarter content">
    <Form @savingTask="saveTask"/>
    <div class="list">
      <Task v-for="(task, index) in tasks" :key="index" :task="task"/>
      <Box v-if="listEmpty">
        Não há nenhuma tarefa
      </Box>
    </div>
  </div>
</main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue'
import Form from './components/Form.vue'
import Task from './components/Task.vue'
import Box from './components/Box.vue'
import ITask from './interface/ITask'
export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    Form,
    Task,
    Box
  },
  data () {
    return{
      tasks: [] as ITask[],
      modeDarkActive: false
    }
  },
  computed: {
    listEmpty () : boolean {
      return this.tasks.length === 0
    }
  },
  methods: {
    saveTask(task: ITask){
      this.tasks.push(task)
    },
    exchangeTheme (modeDarkActive : boolean) {
      this.modeDarkActive = modeDarkActive
    }
  }
});
</script>
<style>
.list {
  padding: 1.5rem;
}
.main {
  --bg-primary: #fff;
  --text-primary: #000;
}
main.mode-dark {
  --bg-primary: #2b2d42;
  --text-primary: #ddd;
}
.content {
  background-color: var(--bg-primary);
}
</style>
