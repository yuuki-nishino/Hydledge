<template>
  <div>
    <BreadCrumb :breadcrumbs="breadcrumbs" />
    <v-container fluid class="hard-intro">
      <section>
        <v-row justify="center">
          <v-col cols="12" md="10">
            <v-row class="my-2">
              <div
                class="
                  text-h4 text-md-h2
                  mx-2
                  my-3
                  font-weight-bold
                  primary--text
                "
              >
                硬度について
              </div>
            </v-row>
            <v-divider></v-divider>
            <v-row class="my-2">
              <v-col cols="12" md="4">
                <h1>はじめに</h1>
              </v-col>
            </v-row>
            <v-row class="my-2 mx-3">
              <div>
                水道水は場所によって硬度が違うことをご存知ですか？
                欧米の国と日本の水の硬度が異なるということをご存知の方は多いかもしれません。<br />
                実は日本の中でも地域によって硬度が違うんです。日本の水道水は平均すると軟水ですが、硬水の地域も存在しています。<br />
                このサイトでは、全国の水道水の硬度を水質検査箇所毎に表示し、
                都道府県の平均硬度や検査地点ごとの硬度をランキングやマッピング、グラフなどで表示しています。<br />
                （※硬度ランキング上位もしくは下位が良い悪いということではありません。）<br /><br />
              </div>
            </v-row>

            <v-row class="my-2">
              <v-col cols="12" md="4">
                <h1>硬度とは？</h1>
              </v-col>
            </v-row>
            <v-row class="my-2 mx-3">
              <v-col cols="12" md="7">
                <div>
                  硬度は水の中の<b>カルシウム</b>と<b>マグネシウム</b>の含有量の指標です。<br />
                  カルシウムとマグネシウムの量を炭酸カルシウム量（CaCo3）に換算した値で、以下の計算式で算出します。
                  <br />
                  <br />
                </div>
                <center>
                  <strong>
                    硬度 (mg/L) ＝カルシウム濃度 (mg/L)×2.5 + マグネシウム濃度
                    (mg/L)×4.1
                  </strong>
                </center>
                <div>
                  <br />
                  <br />
                  硬度が低い水を<b>「軟水」</b>、硬度が高い水を<b>「硬水」</b>といい、WHOの基準では以下のように分類されています。
                  <br /><br />
                </div>
                <v-col cols="12" md="8">
                  <ul>
                    <li>0〜60mg/L未満：<strong>軟水</strong></li>
                    <li>60〜120mg/L未満：<strong>中程度の硬水</strong></li>
                    <li>120〜180mg/L未満：<strong>硬水</strong></li>
                    <li>180mg/L以上：<strong>非常な硬水</strong></li>
                  </ul>
                  <br />
                </v-col>
              </v-col>
              <v-col cols="12" md="5">
                <v-img :src="hard_img_src"></v-img>
              </v-col>
            </v-row>

            <v-row class="my-2">
              <v-col cols="12" md="4">
                <h1>水道水における基準</h1>
              </v-col>
            </v-row>

            <v-row class="my-2">
              <v-col cols="12" md="4">
                <h1>硬度の違いによる特徴</h1>
              </v-col>
            </v-row>

            <v-row class="my-2">
              <v-col cols="12" md="4">
                <h1>硬度データの見方</h1>
              </v-col>
            </v-row>

            <v-row class="my-2 mx-3" justify="center">
              <div class="my-2">
                <v-btn
                  x-large
                  color="#0E2997"
                  dark
                  width="100%"
                  style="text-transform: none"
                  @click="moveData()"
                >
                  <v-icon>mdi-chevron-right</v-icon>
                  <strong>&nbsp;硬度データを見てみよう！</strong>
                </v-btn>
              </div>
            </v-row>
            <v-row class="my-3 mx-3">
              <div>
                <br />
                ※本サイトで使用する水質データは（公社）日本水道協会
                <a
                  href="http://www.jwwa.or.jp/mizu/ent_up.html"
                  target="_blank"
                >
                  「水道水質データベース 2018年給水栓水（平均値)」
                </a>
                を利用しています。<br /><br />

                また、都道府県の平均硬度は各検査地点の配水量を考慮して、
                （硬度）×（配水量）÷（都道府県総配水量） で算出しています。
              </div>
            </v-row>
          </v-col>
        </v-row>
      </section>
    </v-container>
  </div>
</template>

<script scoped>
import BreadCrumb from '~/components/atoms/BreadCrumb.vue'

export default {
  name: 'HardnessHome',
  components: {
    BreadCrumb,
  },
  data() {
    return {
      // JapanData: JapanData,
      hard_img_src: require('@/assets/img/hard_img.jpg'),
    }
  },
  computed: {
    breadcrumbs() {
      return [
        {
          name: 'ホーム',
          path: '/',
        },
        {
          name: '硬度',
        },
      ]
    },
  },
  methods: {
    moveData() {
      this.$router.push('/hardness/data/')
    },
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

h1 {
  position: relative;
  background: #f1f8ff;
  padding: 0.25em 0.5em;
  border-left: solid 2em #5c9ee7;
  width: 100%;
}

h1::before {
  content: url('@/assets/img/icon/water-check.png');
  position: absolute;
  color: white;
  left: -1.8em;
  top: 60%;
  transform: translateY(-50%);
}

ul,
ol {
  color: #0e2997;
  border: dashed 2px #668ad8;
  background: #f1f8ff;
  padding: 0.5em 0.5em 0.5em 2em;
  width: 110%;
}

ul li,
ol li {
  line-height: 1.5;
  padding: 0.5em 0;
}
</style>