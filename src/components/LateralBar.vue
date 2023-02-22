<template>
  <header>
      <h1>
        <img src="../assets/logo2.png" alt="">  
      </h1>
      <button class="button" @click="changeTheme">
        {{ textButtom }}
      </button>
  </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'LateralBar',
  emits: ['whenThemeChanged'],
  data(){
    return { 
      darkModeEnabled: false
    }
  },
  computed: {
    textButtom () {
      if (this.darkModeEnabled) {
        return 'Disable Dark Mode'
      }
      return 'Enable Dark Mode'
    }
  },
  methods: {
    changeTheme () {
      this.darkModeEnabled = !this.darkModeEnabled
      this.$emit('whenThemeChanged', this.darkModeEnabled)
    }
  }
})
</script>

<style scoped>
header {
  padding: 1rem;
  background: #0d3b66;
  width: 100%;
  height: 100vh;
}
@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>