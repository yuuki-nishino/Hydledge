<template>
  <v-container fluid>
    <v-row>
      <v-col cols="8">
        <div class="text-h5 my-3 font-weight-bold primary--text">
          都道府県ごとの硬度平均
        </div>
        <v-card class="ml-5 mb-2">
          <GChart
            :settings="chartSettings"
            :type="chartType"
            :data="chartData"
            :options="chartOptions"
            :events="chartEvents"
          />
        </v-card>
        <v-card class="ml-5" height="300">
          <GChart
            :type="chartType2"
            :data="chartData"
            :options="chartOptions2"
          />
        </v-card>
      </v-col>
      <v-col cols="4">
        <div class="text-h5 my-3 font-weight-bold primary--text">
          各都道府県の詳細
        </div>
        <v-row>
          <v-col cols="5" class="text-center">
            <h3>北海道・東北地方</h3>
            <div v-for="region in tohoku" :key="region.index">
              <NuxtLink
                :to="{ path: `/pref`, query: { prefName: region.name } }"
                class="mx-1"
              >
                {{ region.name }}</NuxtLink
              >
            </div>
          </v-col>
          <v-col cols="5" class="text-center">
            <h3>関東地方</h3>
            <div v-for="region in kanto" :key="region.index">
              <NuxtLink
                :to="{ path: `/pref`, query: { prefName: region.name } }"
                class="mx-1"
              >
                {{ region.name }}</NuxtLink
              >
            </div>
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="5" class="text-center">
            <h3>中部地方</h3>
            <div v-for="region in chubu" :key="region.index">
              <NuxtLink
                :to="{ path: `/pref`, query: { prefName: region.name } }"
                class="mx-1"
              >
                {{ region.name }}</NuxtLink
              >
            </div>
          </v-col>
          <v-col cols="5" class="text-center">
            <h3>近畿地方</h3>
            <div v-for="region in kinki" :key="region.index">
              <NuxtLink
                :to="{ path: `/pref`, query: { prefName: region.name } }"
                class="mx-1"
              >
                {{ region.name }}</NuxtLink
              >
            </div>
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="5" class="text-center">
            <h3>中国・四国地方</h3>
            <div v-for="region in chugokushikoku" :key="region.index">
              <NuxtLink
                :to="{ path: `/pref`, query: { prefName: region.name } }"
                class="mx-1"
              >
                {{ region.name }}</NuxtLink
              >
            </div>
          </v-col>
          <v-col cols="5" class="text-center">
            <h3>九州地方</h3>
            <div v-for="region in kyushu" :key="region.index">
              <NuxtLink
                :to="{ path: `/pref`, query: { prefName: region.name } }"
                class="mx-1"
              >
                {{ region.name }}</NuxtLink
              >
            </div>
          </v-col>
        </v-row>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import { GChart } from 'vue-google-charts'
import JapanData from '@/assets/mockup_data/JapanHardness.json'

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
      chartData: JapanData,
      chartOptions: {
        region: 'JP',
        resolution: 'provinces',
        displayMode: 'regions',
        colors: ['white', '#0E2997'],
        width: '100%',
        height: '100%',
        magnifyingGrass: { enable: true, zoomFactor: 7.5 },
      },
      chartEvents: {
        // select: () => {
        //   alert('クリックしました')
        // },
      },
      chartOptions2: {
        chart: {
          title: '都道府県別人口',
        },
        width: '100%',
        height: '300',
      },

      tohoku: [
        { name: '北海道' },
        { name: '青森県' },
        { name: '岩手県' },
        { name: '秋田県' },
        { name: '宮城県' },
        { name: '山形県' },
        { name: '福島県' },
      ],
      kanto: [
        { name: '茨城県' },
        { name: '栃木県' },
        { name: '群馬県' },
        { name: '埼玉県' },
        { name: '千葉県' },
        { name: '東京都' },
        { name: '神奈川県' },
      ],
      chubu: [
        { name: '新潟県' },
        { name: '富山県' },
        { name: '石川県' },
        { name: '福井県' },
        { name: '長野県' },
        { name: '岐阜県' },
        { name: '山梨県' },
        { name: '静岡県' },
        { name: '愛知県' },
      ],
      kinki: [
        { name: '滋賀県' },
        { name: '三重県' },
        { name: '京都府' },
        { name: '大阪府' },
        { name: '奈良県' },
        { name: '和歌山県' },
        { name: '兵庫県' },
      ],
      chugokushikoku: [
        { name: '鳥取県' },
        { name: '岡山県' },
        { name: '島根県' },
        { name: '広島県' },
        { name: '山口県' },
        { name: '香川県' },
        { name: '愛媛県' },
        { name: '徳島県' },
        { name: '高知県' },
      ],
      kyushu: [
        { name: '福岡県' },
        { name: '佐賀県' },
        { name: '長崎県' },
        { name: '大分県' },
        { name: '熊本県' },
        { name: '宮崎県' },
        { name: '鹿児島県' },
        { name: '沖縄県' },
      ],
    }
  },
}
</script>
