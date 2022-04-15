<template>
  <div class="container">
    <v-row>
      <GChart
        :settings="chartSettings"
        :type="chartType"
        :data="chartData"
        :options="chartOptions"
      />
      <GChart :type="chartType2" :data="chartData" :options="chartOptions2" />
    </v-row>
  </div>
</template>

<script>
import { GChart } from 'vue-google-charts'

export default {
  name: 'IndexPage',
  components: {
    GChart,
  },
  data() {
    return {
      chartSettings: {
        packages: ['geochart'],
      },
      chartType: 'GeoChart',
      chartType2: 'ColumnChart',
      chartData: [
        ['都道府県', '人口'],
        ['北海道', 5224614],
        ['青森', 1237984],
        ['岩手', 1210534],
        ['宮城', 2301996],
        ['秋田', 959502],
        ['山形', 1068027],
        ['福島', 1833152],
        ['茨城', 2867009],
        ['栃木', 1933146],
        ['群馬', 1939110],
        ['埼玉', 7344765],
        ['千葉', 6284480],
        ['東京', 14047594],
        ['神奈川', 9237337],
        ['新潟', 2201272],
        ['富山', 1034814],
        ['石川', 1132526],
        ['福井', 766863],
        ['山梨', 809974],
        ['長野', 2048011],
        ['岐阜', 1948742],
        ['静岡', 3633202],
        ['愛知', 7542415],
        ['三重', 1770254],
        ['滋賀', 1413610],
        ['京都', 2578087],
        ['大阪', 8837685],
        ['兵庫', 5465002],
        ['奈良', 1324473],
        ['和歌山', 922584],
        ['鳥取', 553407],
        ['島根', 671527],
        ['岡山', 1888432],
        ['広島', 2799702],
        ['山口', 1342059],
        ['徳島', 719559],
        ['香川', 950244],
        ['愛媛', 1344841],
        ['高知', 691527],
        ['福岡', 5135214],
        ['佐賀', 811442],
        ['長崎', 1312317],
        ['熊本', 1738301],
        ['大分', 1123852],
        ['宮崎', 1069576],
        ['鹿児島', 1588256],
        ['沖縄', 1467480],
      ],
      chartOptions: {
        region: 'JP',
        resolution: 'provinces',
        displayMode: 'regions',
        colors: ['white', 'blue'],
        width: '500',
        height: '600',
      },
      chartOptions2: {
        chart: {
          title: '都道府県別人口',
        },
        width: '600',
        height: '500',
      },
    }
  },
}
</script>
