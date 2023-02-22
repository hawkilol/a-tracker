<template>
    <div class="box has-text-weight-bold" :style="styles">
        <slot>

        </slot>
    </div>
</template>

<script lang="ts">

import { defineComponent } from 'vue';
export default defineComponent({
    name: 'Box',
    data() {
        return {
            styles: {
                backgroundColor: '#F8B195'
            }
        }
    }
})

</script>

<!--.box {background: #F8B195;}-->

<style scoped>

</style>
