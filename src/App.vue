<template>
  <div id="app">
    <form-table />
  </div>
</template>

<script>
import FormTable from './components/FormTable.vue'

export default {
  name: 'App',
  components: {
    FormTable
  }
}
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
