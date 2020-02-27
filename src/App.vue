<template>
  <div id="app">
    <h1>Energy Data</h1>
  </div>
</template>

<script>


export default {
  name: 'App',
  data() {
    return {
      energyTypes: {}
    }
  },
  mounted() {
  fetch('https://api.carbonintensity.org.uk/generation')
  .then(res => res.json())
  .then(energyTypes => this.energyTypes = energyTypes)
  }
}

</script>

<style>
#app {

}
</style>
