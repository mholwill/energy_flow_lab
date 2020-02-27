<template lang="html">
  <GChart class="chart"
  type="PieChart"
  :data="chartData"
  :options="chartOptions"
  />
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
        chart: {
          title: 'Title',
          subtitle: 'Subtitle'
        }
      }
    }
  },
  props: ['formattedFuels'],
  components: {
    GChart
  }
}
</script>
<style lang="css" scoped>

 .chart {
   width: 50%;
   height: auto;
 }
</style>
