<template>
    <Box>
        <div class="columns">
            <div class="column is-7">
                {{ task.description || 'Task With No Description'}}
            </div>
            <div class="column">
                <Cronometer :timeInSeconds= "task.durationInSeconds"/>
            </div>
        </div>
    </Box>
</template>

<script lang="ts">
import ITask from '@/intefaces/ITask';
import { defineComponent, DefineComponent, PropType} from 'vue';
import Box from './Box.vue';


import Cronometer from './Cronometer.vue';

export default defineComponent({
    name: "Task",
    components: {
    Cronometer,
    Box
},
    props:{
        task: {
            type: Object as PropType<ITask>,
            required: true
        }
    }
});

</script>""
<style scoped>
.box{
    background: #F8B195;
}


</style>