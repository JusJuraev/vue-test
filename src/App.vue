<template>
  <cities-table />
</template>

<script>
  import CitiesTable from '@/components/CitiesTable'

  export default {
    name: 'App',
    components: {
      CitiesTable
    }
  }
</script>

<style>
  * {
    box-sizing: border-box;
  }
  body {
    margin: 0;
    padding: 0;
  }
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
  }
</style>
