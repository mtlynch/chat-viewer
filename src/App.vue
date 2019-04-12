<template>
  <div id="app" class="container">
    <LogViewer/>
  </div>
</template>

<script>
import LogViewer from './components/LogViewer.vue'

export default {
  name: 'app',
  components: {
    LogViewer
  }
}
</script>

<style>
#app {
  font-size: 11pt;
}
</style>
