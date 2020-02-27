<template>
  <div id="app">
    <h1>Energy Data</h1>
    <fuel-chart :formattedFuels="formattedFuels"/>
  </div>
</template>

<script>
import FuelsChart from './components/FuelsChart.vue'


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
      this.formattedFuels.unshift(["Fuel", "Percentage"])
    }
  },
  components: {
    "fuel-chart": FuelsChart
  },
  mounted() {
  fetch('https://api.carbonintensity.org.uk/generation')
  .then(res => res.json())
  .then((energyTypes) => {
    this.energyTypes = energyTypes;
    this.formatFuel(energyTypes.data.generationmix);
  })
  }
}

</script>

<style>
#app {

}
</style>
