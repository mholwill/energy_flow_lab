<template>
  <div id="app">
    <h1>Energy Data</h1>
    <h2>{{this.formattedFuels}}</h2>

  </div>
</template>

<script>


export default {
  name: 'App',
  data() {
    return {
      energyTypes: {},
      formattedFuels: []
    }
  },
  methods: {
    formatFuel: function(fuelObjects) {
      fuelObjects.forEach((fuelObject) => {
        let newArray = []
        newArray.push(fuelObject.fuel)
        newArray.push(fuelObject.perc)
        this.formattedFuels.push(newArray)
      })
    }
  },
  mounted() {
  fetch('https://api.carbonintensity.org.uk/generation')
  .then(res => res.json())
  .then((energyTypes) => {
    this.energyTypes = energyTypes;
    this.formatFuel(energyTypes.data.generationmix);
    console.log(this.energyTypes);
    console.log(this.formattedFuels);
  })
  }
}

</script>

<style>
#app {

}
</style>
