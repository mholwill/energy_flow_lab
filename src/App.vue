<template>
  <div id="app">
    <h1>Energy Data</h1>
    <h2>{{this.energyTypes.data.from.substring(0, 16)}} to {{this.energyTypes.data.to.substring(0, 16)}}</h2>
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
*{
  padding: 0px;
  margin: 0px;
}
#app {
  width: 100vw;
  height: 100vh;
  font-family: 'Montserrat';
  text-align: center;
}

h1 {
  margin-bottom: 40px;
}



</style>
