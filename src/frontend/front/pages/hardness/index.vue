<template>
  <v-container fluid class="hard-intro">
    <section>
      <v-row class="ml-5 my-5">
        <div class="text-h4 my-3 font-weight-bold primary--text">
          硬度 (Hardness)
        </div>
      </v-row>
      <v-row class="my-5 mx-10">
        <div>
          水道水は場所によって硬度が違うことをご存知ですか？
          日本の水道水は平均すると軟水ですが、硬水の地域も存在しています。<br />
          このサイトでは、全国の水道水の硬度を水質検査箇所毎に表示し、
          都道府県の平均硬度や検査地点ごとの硬度をランキング形式で表示しています。<br />
          （ランキング上位が良い悪いではありません）<br /><br />

          <h3>硬度とは?</h3>
          硬度は水の中のカルシウムとマグネシウムの含有量の指標です。<br />
          硬度はカルシウムとマグネシウムの量を炭酸カルシウム量（CaCo3）に換算した値で、以下の計算式で算出します。
          <br />
          <br />
          硬度 (mg/L) ＝カルシウム濃度 (mg/L)×2.5 + マグネシウム濃度 (mg/L)×4.1
          <br />
          <br />
          硬度が低い水を「軟水」、硬度が高い水を「硬水」といい、WHOの基準では以下のように分類されています。
          <br />
          <ul>
            <li>0〜60mg/L未満：軟水</li>
            <li>60〜120mg/L未満：中程度の硬水</li>
            <li>120〜180mg/L未満：硬水</li>
            <li>180mg/L以上：非常な硬水</li>
          </ul>
          <br />
          日本の水道水は平均すると軟水ですが、硬水の地域も存在しています。<br />

          <br />
          ※本サイトで使用する水質データは（公社）日本水道協会
          <a href="http://www.jwwa.or.jp/mizu/ent_up.html">
            「水道水質データベース 2018年給水栓水（平均値)」
          </a>
          を利用しています。<br /><br />

          また、都道府県の平均硬度は各検査地点の配水量を考慮して、
          （硬度）×（配水量）÷（都道府県総配水量） で算出しています。
        </div>
      </v-row>
    </section>
    <v-divider></v-divider>
    <v-row class="my-5">
      <v-col cols="12" md="6">
        <div class="text-h4 my-3 font-weight-bold primary--text text-center">
          硬度ランキング
        </div>
        <v-row justify="center" class="my-3">
          <v-card width="90%">
            <v-simple-table fixed-header height="680">
              <thead>
                <tr>
                  <th style="text-align: center">順位</th>
                  <th style="text-align: center">都道府県名</th>
                  <th style="text-align: center">平均硬度</th>
                  <th style="text-align: center">詳細ページ</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="i in 47" :key="i">
                  <td style="text-align: center">{{ i }}</td>
                  <td style="text-align: center">{{ SortedData[i][0] }}</td>
                  <td style="text-align: center">{{ SortedData[i][1] }}</td>
                  <td style="text-align: center">
                    <nuxt-link
                      :to="{
                        path: `/hardness/pref`,
                        query: { prefName: SortedData[i][0] },
                      }"
                      tag="div"
                      class="c-p"
                    >
                      <v-btn elevation="1" color="primary">詳細ページ</v-btn>
                    </nuxt-link>
                  </td>
                </tr>
              </tbody>
            </v-simple-table>
          </v-card>
        </v-row>
      </v-col>
      <v-col cols="12" md="6">
        <div class="text-h4 my-3 font-weight-bold primary--text text-center">
          硬度平均マップ
        </div>
        <v-card class="ml-5 mb-10" elevation="1">
          <GChart
            :settings="chartSettings"
            :type="chartType"
            :data="chartData"
            :options="chartOptions"
            :events="chartEvents"
          />
        </v-card>
        <div class="text-h4 my-3 font-weight-bold primary--text text-center">
          各都道府県の詳細ページ
        </div>
        <v-row justify="center" class="my-3 mb-10">
          <v-card width="80%">
            <v-row justify="center" class="my-3">
              <v-col cols="8" align-self="center">
                <v-row class="mt-2">
                  <v-select
                    v-model="selectedPref"
                    :items="PrefArray"
                    outlined
                    label="都道府県を選択"
                  ></v-select>
                </v-row>
                <v-row justify="center" class="mb-2">
                  <nuxt-link
                    :to="{
                      path: `/hardness/pref`,
                      query: { prefName: selectedPref },
                    }"
                    tag="div"
                    class="c-p"
                  >
                    <v-btn x-large elevation="1" color="primary"
                      >詳細ページに移動</v-btn
                    >
                  </nuxt-link>
                </v-row>
              </v-col>
            </v-row>
          </v-card>
        </v-row>
      </v-col>
    </v-row>
    <v-divider></v-divider>

    <section>
      <v-row class="ml-5 my-5">
        <v-col cols="12">
          <div class="text-h4 my-3 font-weight-bold primary--text text-center">
            硬度が高い＆低い地点ランキング(TOP50)
          </div>
        </v-col>
      </v-row>
      <v-row justify="center" class="my-5">
        <div class="text-h5 font-weight-bold primary--text text-center">
          硬度が高い地点 (硬水ランキング)
        </div>
      </v-row>
      <v-row justify="center" class="mb-5">
        <v-card width="80%">
          <v-simple-table fixed-header height="530">
            <thead>
              <tr>
                <th style="text-align: center">順位</th>
                <th style="text-align: center">事業主体名</th>
                <th style="text-align: center">浄水場名</th>
                <th style="text-align: center">水源名</th>
                <th style="text-align: center">平均硬度</th>
                <th style="text-align: center">詳細ページ</th>
              </tr>
            </thead>
            <tbody>
              <tr
                v-for="(hard_item, index) in hard_top10_lists"
                :key="hard_item.facility"
              >
                <td style="text-align: center">{{ index + 1 }}</td>
                <td style="text-align: center">
                  {{ hard_item.pref }} {{ hard_item.district }}
                </td>
                <td style="text-align: center">{{ hard_item.facility }}</td>
                <td style="text-align: center">
                  {{ hard_item.origin }}
                </td>
                <td style="text-align: center">
                  <b>{{ hard_item.hardness }}</b>
                </td>
                <td style="text-align: center">
                  <nuxt-link
                    :to="{
                      path: `/hardness/pref`,
                      query: { prefName: hard_item.pref },
                    }"
                    tag="div"
                    class="c-p"
                  >
                    <v-btn elevation="1" color="primary">詳細ページ</v-btn>
                  </nuxt-link>
                </td>
              </tr>
            </tbody>
          </v-simple-table>
        </v-card>
      </v-row>
      <v-row justify="center" class="my-5">
        <div class="text-h5 mt-5 font-weight-bold primary--text text-center">
          硬度が低い地点 (軟水ランキング)
        </div>
      </v-row>
      <v-row justify="center" class="mb-5">
        <v-card width="80%">
          <v-simple-table fixed-header height="530">
            <thead>
              <tr>
                <th style="text-align: center">順位</th>
                <th style="text-align: center">事業主体名</th>
                <th style="text-align: center">浄水場名</th>
                <th style="text-align: center">水源名</th>
                <th style="text-align: center">平均硬度</th>
                <th style="text-align: center">詳細ページ</th>
              </tr>
            </thead>
            <tbody>
              <tr
                v-for="(soft_item, index) in soft_top10_lists"
                :key="soft_item.facility"
              >
                <td style="text-align: center">{{ index + 1 }}</td>
                <td style="text-align: center">
                  {{ soft_item.pref }} {{ soft_item.district }}
                </td>
                <td style="text-align: center">{{ soft_item.facility }}</td>
                <td style="text-align: center">
                  {{ soft_item.origin }}
                </td>
                <td style="text-align: center">
                  <b>{{ soft_item.hardness }}</b>
                </td>
                <td style="text-align: center">
                  <nuxt-link
                    :to="{
                      path: `/hardness/pref`,
                      query: { prefName: soft_item.pref },
                    }"
                    tag="div"
                    class="c-p"
                  >
                    <v-btn elevation="1" color="primary">詳細ページ</v-btn>
                  </nuxt-link>
                </td>
              </tr>
            </tbody>
          </v-simple-table>
        </v-card>
      </v-row>
    </section>
    <v-row>
      <v-card class="mx-5 my-10" height="300" width="100%">
        <GChart :type="chartType2" :data="chartData" :options="chartOptions2" />
      </v-card>
    </v-row>
  </v-container>
</template>

<script scoped>
import { GChart } from 'vue-google-charts'
// import JapanData from '@/assets/mockup_data/HardnessData/JapanHardness.json'
import ChartHardness from '@/assets/mockup_data/HardnessData/ChartHardness.json'
import RankedData from '@/assets/mockup_data/HardnessData/RankedJapanHardness.json'
import HardRanking from '@/assets/mockup_data/HardnessData/hardness_point_ranking.json'
import SoftRanking from '@/assets/mockup_data/HardnessData/hardness_point_ranking2.json'

export default {
  name: 'HardnessHome',
  components: {
    GChart,
  },
  data() {
    return {
      // JapanData: JapanData,
      chartSettings: {
        packages: ['geochart'],
      },
      chartType: 'GeoChart',
      chartType2: 'ColumnChart',
      chartData: ChartHardness,
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
        explorer: {
          actions: ['dragToZoom', 'rightClickToReset'],
          axis: 'horizontal',
        },
      },

      SortedData: RankedData,

      PrefArray: [
        '北海道',
        '青森県',
        '岩手県',
        '宮城県',
        '秋田県',
        '山形県',
        '福島県',
        '茨城県',
        '栃木県',
        '群馬県',
        '埼玉県',
        '千葉県',
        '東京都',
        '神奈川県',
        '新潟県',
        '富山県',
        '石川県',
        '福井県',
        '山梨県',
        '長野県',
        '岐阜県',
        '静岡県',
        '愛知県',
        '三重県',
        '滋賀県',
        '京都府',
        '大阪府',
        '兵庫県',
        '奈良県',
        '和歌山県',
        '鳥取県',
        '島根県',
        '岡山県',
        '広島県',
        '山口県',
        '徳島県',
        '香川県',
        '愛媛県',
        '高知県',
        '福岡県',
        '佐賀県',
        '長崎県',
        '熊本県',
        '大分県',
        '宮崎県',
        '鹿児島県',
        '沖縄県',
      ],
      selectedPref: '',
      hard_top10_lists: HardRanking,
      soft_top10_lists: SoftRanking,
    }
  },
}
</script>

<style scoped>
.c-p {
  cursor: pointer;
}

.hard-intro {
  background: rgba(242 242 242);
  width: 100%;
}
</style>