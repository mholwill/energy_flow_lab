<template lang="html">
  <div>
    <GChart class="chart"
    :type="chartType"
    :data="chartData"
    :options="chartOptions"
    />
    <label for="list-item">Select a chart:</label>
    <select class="list-item" name="list-item" v-model="chartType">
      <option value="ColumnChart">Column Chart</option>
      <option value="LineChart">Line Chart</option>
      <option value="PieChart">Pie Chart</option>
    </select>
  </div>
</template>

<script>
import {GChart} from 'vue-google-charts'

export default {
  name: "fuel-chart",
  data(){
    return {
      chartData: this.formattedFuels,
      // chartData: this.formattedFuels,
      chartOptions: {
        title: 'Energy Ratings',
        subtitle: 'Subtitle',
        // is3D: true,
        pieHole: 0.4,
        backgroundColor: 'transparent',
        legend: {
          textStyle: {
            fontName: 'Montserrat',
          }
        }
      },
      chartType: 'PieChart'
    }
  },
  props: ['formattedFuels'],
  components: {
    GChart
  }
}
</script>

<style lang="css" scoped>
* {
  font-family: 'Montserrat', sans-serif;
}
  .chart {
    width: 900px;
    height: 500px;
    border: solid black 4px;
    border-radius: 80px;
    margin: auto;
    background-color: lightgrey;
  }



</style>
