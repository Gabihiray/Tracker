<template>
    <Box>
        <div class="columns">
            <div class="column is-7">
                {{ task.description || 'Tarefa sem descrição' }}
            </div>
            <div class="column">
                <stopWatcher :timeSeconds="task.durationSeconds"/>
            </div>
        </div>
    </Box>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import StopWatcher from './StopWatcher.vue'
import Box from './Box.vue'
import ITask from '../interface/ITask'
export default defineComponent ({
    name: "Task-vue",
    components: {
        StopWatcher,
        Box
    },
    props: {
        task: {
            type: Object as PropType<ITask>,
            required: true
        }
    }
})

</script>