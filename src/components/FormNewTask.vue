
<template>
    <div class="box form">
      <div class="columns">
        <div
          class="column is-8"
          role="form"
          aria-label="Formulário para criação de uma nova tarefa"
        >
          <input
            type="text"
            class="input"
            placeholder="Qual tarefa você deseja iniciar?"
            v-model="description"
          />
        </div>
        <div class="column">
          <Timer @TimerEnded="endTask"/>
        </div>
      </div>
    </div>
  </template>
<script lang="ts">
import { defineComponent } from 'vue'
import  Timer  from './Timer.vue'

export default defineComponent({
    name: "FormNewTask",
    emits: ['whenSaveTask'],
    components:{
        Timer
    },
    data() {
        return {
            description: ''
        }
    },
    
    methods: {
        endTask (timeElapsed: number): void {
            this.$emit('whenSaveTask', {
              durationInSeconds: timeElapsed,
              description: this.description
            })
            console.log('Task Time: ', timeElapsed)
            console.log('Task Description:', this.description)

            this.description = ''
            
        }
    }
});
</script>

<style>
.form {
  color: var(--texto-primario);
  background-color: var(--bg-primario);
}
</style>