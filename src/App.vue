<template>
  <main class="columns is-gapless is-multiline" :class ="{'dark-mode': darkModeEnabled}">
    <div class="column is-one-quarter">
      <LateralBar @whenThemeChanged="changeTheme"/>
    </div>
    <div class="column is-three-quarter content">
      <FormNewTask @whenSaveTask ="saveTask"/>
      <div class="list">
        <!-- Lista de Tarefas ???? -->
        <Task v-for="(task, index) in tasks" :key="index" :task="task"></Task>
        <Box v-if="listIsEmpty">
          Not Very Stonks today >:(
        </Box>
      </div>
        
      
      
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import LateralBar from './components/LateralBar.vue'
import FormNewTask from './components/FormNewTask.vue'
import Task from './components/Task.vue';
import ITask from './intefaces/ITask';
import Box from './components/Box.vue';


export default defineComponent({
  name: 'App',
  components: {
    LateralBar,
    FormNewTask,
    Task,
    Box
},
  data(){
    return{
      tasks: [] as ITask[],
      darkModeEnabled: false
    }
  },
  computed:{
    listIsEmpty(): boolean {
      return this.tasks.length === 0
    }
  },
  methods:{
    saveTask (task: ITask){
      this.tasks.push(task)
    },
    changeTheme(darkModeEnabled: boolean){
      this.darkModeEnabled = darkModeEnabled
    }
  }
});
</script>

<style>
.list {
  padding: 1.25rem;

}

main {
  --bg-primario: #fff;
  --texto-primario: #000;
}

main.dark-mode {
  --bg-primario: #2b2d42;
  
  --texto-primario: #ddd;
}

.content {
  background-color: var(--bg-primario);
}

</style>