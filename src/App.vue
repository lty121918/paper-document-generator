<template>
  <div id="app">
    <Literature></Literature>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Literature from './components/Literature.vue'

export default {
  name: 'App',
  components: {
    Literature
  },

}
</script>

<style lang="less">
#app {
    display: flex;
    align-items: center;
    justify-content: center;
}
</style>
