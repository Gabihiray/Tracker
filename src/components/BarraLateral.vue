<template>
    <header>
        <h1>
            <img src="../assets/logo.png" alt="logo">
        </h1>
        <button class="button" @click="updateTheme">
            {{ textButton }}
        </button>
    </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
    name: 'App',
    emits: ['themeChange'],
    data () {
        return {
            modeDarkActive: false,
        }
    },
    computed: {
        textButton () {
            if (this.modeDarkActive) {
                return 'Desativar modo escuro'
            }
            return 'Ativar modo escuro'
        }
    },
    methods: {
        updateTheme () {
            this.modeDarkActive = !this.modeDarkActive
            this.$emit('themeChange', this.modeDarkActive)
        }
    }
});
</script>

<style scoped>
header {
    padding: 1rem;
    background: #0d3b66;
    width: 100%;
    height: 100vh;
    text-align: center;
}
@media only screen and (max-width: 768px) {
    header {
        padding: 2.5rem;
        height: auto;
    }    
}
</style>