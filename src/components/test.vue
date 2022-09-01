<template lang="">
   <div>
      <highcharts :options="chartOptions"></highcharts>
   </div>
</template>
<script>
   import {Chart} from 'highcharts-vue'
export default {
   data() {
    return {
      chartOptions: {
        series: [{
          data: [1,2,3,4] // sample data
        }]
      }
    }
  },
  components: {
    highcharts: Chart 
  }
}
</script>
<style lang="">
   
</style>