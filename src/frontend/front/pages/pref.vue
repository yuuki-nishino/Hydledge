<template>
  <v-container fluid>
    <div class="text-h3 my-3 font-weight-bold primary--text">
      {{ $route.query.prefName }}
    </div>
    <v-row class="my-3">
      <v-col cols="6">
        <v-card height="500">
          <iframe
            src="https://www.google.com/maps/d/embed?mid=102raZYf3j_ylyldshZ5zBOq80K4o9Yc&ehbc=2E312F&z=9&ll=36.091222344366145%2C138.1945726612066"
            width="100%"
            height="100%"
            allowfullscreen
          ></iframe>
        </v-card>
      </v-col>
      <v-col cols="6">
        <v-card height="250">
          <GChart :type="HistoType" :data="chartData" :options="HistOptions" />
        </v-card>
        <v-card height="250">
          <GChart
            :type="ColumnType"
            :data="chartData"
            :options="ColumnOptions"
          />
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import { GChart } from 'vue-google-charts'
import NaganoData from '@/assets/mockup_data/NaganoHardness.json'

export default {
  name: 'PrefPage',
  components: {
    GChart,
  },
  data() {
    return {
      chartData: NaganoData,
      HistoType: 'Histogram',
      ColumnType: 'ColumnChart',

      HistOptions: {
        title: '長野県内の事業主体ごとの硬度分布',
        width: '100%',
        height: '100%',
      },
      ColumnOptions: {
        title: '長野県内の事業主体ごとの硬度グラフ',
        width: '100%',
        height: '100%',
      },
    }
  },
}
</script>