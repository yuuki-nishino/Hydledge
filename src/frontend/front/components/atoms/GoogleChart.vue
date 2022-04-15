<template>
  <GChart :type="chartType" :data="chartData" :options="chartOptions" />
</template>

<script>
import { GChart } from 'vue-google-charts'

export default {
  components: {
    GChart,
  },
  props: {
    // chartSettings: {
    //   type: Object,
    //   default: () => {
    //     return {}
    //   },
    // },
    chartType: {
      type: String,
      default: '',
    },
    chartData: {
      type: Array,
      default: () => {
        return []
      },
    },
    chartOptions: {
      type: Object,
      default: () => {
        return {}
      },
    },
  },
}
</script>
