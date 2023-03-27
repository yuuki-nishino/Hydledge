<template>
  <div>
    <BreadCrumb :breadcrumbs="breadcrumbs" />
    <v-container fluid class="charge-intro">
      <section>
        <v-row justify="center">
          <v-col cols="12" md="8">
            <v-row class="my-2">
              <div
                class="text-h4 text-md-h2 mx-2 my-3 font-weight-bold primary--text"
              >
                水道料金について
              </div>
            </v-row>
            <v-divider></v-divider>
            <v-row class="my-2">
              <v-col cols="12" md="5">
                <h1>はじめに</h1>
              </v-col>
            </v-row>
            <v-row class="my-2 mx-3">
              <div>
                水道料金が自治体によって異なることをご存知の方は多いのではないかと思います。<br />
                では、どれだけ違いがあるのでしょうか？<br />
                自治体ごとの水道料金をランキングしたWebページはすでにあったりしますが、そのデータを詳しく見ることはできません。<br />
                このサイトでは、全国の自治体における水道料金や都道府県の平均水道料金についてランキング形式で表示しています。
                また、口径や水量による違いも表示したり、基本料金と超過料金のデータについて表示しています。<br />
              </div>
            </v-row>
            <v-row class="mt-2">
              <v-col cols="12" md="5">
                <h1>目次</h1>
              </v-col>
            </v-row>
            <v-row class="mb-5">
              <v-col cols="12" md="10" class="ml-10">
                <ol color="rgba(242 242 242)">
                  <li>
                    <router-link to="/charge#intro"
                      >水道事業と水道料金</router-link
                    >
                  </li>
                  <li>
                    <router-link to="/charge#how">
                      水道料金算定の仕組み
                    </router-link>
                  </li>
                  <li>
                    <router-link to="/charge#variant">口径と使用量</router-link>
                  </li>
                  <li id="intro">
                    <router-link to="/charge#data"
                      >水道料金データの見方</router-link
                    >
                  </li>
                </ol>
              </v-col>
            </v-row>
            <v-divider></v-divider>
            <v-row class="my-2">
              <v-col cols="12" md="5">
                <h1>水道事業と水道料金</h1>
              </v-col>
            </v-row>
            <v-row class="my-2 mx-3">
              <div>
                水道料金を決めている水道事業とはどんな事業なのでしょうか？<br />
                水道事業は、地方公共団体が住民の福祉の増進を目的として設定し、経営する地方公営企業として運営されています。<br />
              </div>
              <div class="box1">
                <p>
                  &emsp;
                  地方公共団体は、一般的な行政活動の他、水の供給や公共輸送の確保、医療の提供、
                  下水の処理など地域住民の生活や地域の発展に不可欠なサービスを提供する様々な事業活動を行っている。
                  こうした事業を行うために地域公共団体が経営する企業活動を総称して「地方公営企業」と呼んでおり、
                  水道事業、下水道事業、交通事業、病院事業等がその代表的なものであるが、
                  その他にも、電気（卸売）・ガス事業や土地造成事業を行うなど、その事業種別は多種多様である。
                </p>
              </div>
              <div>
                参考：
                <a
                  href="https://www.soumu.go.jp/main_sosiki/c-zaisei/kouei.html"
                  target="_blank"
                >
                  総務省「地方公営企業等」
                </a>
              </div>
              <div class="my-10">
                地方公営企業である水道事業は、法律で「<strong>地方公営企業の経営に伴う収入をもつて充てなければならない</strong>」（
                <a
                  href="https://elaws.e-gov.go.jp/document?lawid=327AC0000000292#Mp-At_17_2"
                  target="_blank"
                  >地方公営企業法第17条の2第2項</a
                >
                ）と規定されていて、基本的には水道料金等の事業収入で経営しなければならない原則があります。
              </div>
              <div>
                また、水道料金は、「<strong
                  >公正妥当なものでなければならず、かつ、能率的な経営の下における適正な原価を基礎とし、
                  地方公営企業の健全な運営を確保することができるものでなければならない</strong
                >（
                <a
                  href="https://elaws.e-gov.go.jp/document?lawid=327AC0000000292#Mp-At_21"
                  target="_blank"
                  >地方公営企業法第21条第2項</a
                >
                ）」、「<strong>定率または定額をもって明確に定められていること</strong>」、
                「<strong
                  >特定の者に対して不当な差別的取り扱いをするものでないこと </strong
                >」、等（
                <a
                  href="https://elaws.e-gov.go.jp/document?lawid=332AC0000000177#Mp-At_14"
                  target="_blank"
                  >水道法第14条第2項各号</a
                >
                ）、公正妥当であることが求められています。
              </div>
              <div id="how" class="my-10">
                では、水道料金はどのように決められるのでしょうか？
              </div>
            </v-row>

            <v-divider></v-divider>
            <v-row class="my-2">
              <v-col cols="12" md="5">
                <h1>水道料金算定の仕組み</h1>
              </v-col>
            </v-row>
            <v-row class="my-2 mx-3">
              <h2 class="primary--text">総括原価</h2>
            </v-row>
            <v-row class="my-2 mx-3">
              <div><strong>総括原価 = 営業費用 + 資本費用</strong></div>
              <div class="my-5">
                料金算定期間中における料金総収入額は、適正な原価に基づき算定されなければなりません。
                この場合の原価は、営業費用のほか資本費用をも含むものであり、
                これが通常、総括原価と言われるところから、料金総収入額は、総括原価に等しいものとして決定されます。
              </div>
              <div class="my-3">
                <strong>営業費用：人件費、修繕費、減価償却費など</strong><br />
                <strong>資本費用：支払利息、資本維持費</strong><br />
                ※資産維持費：施設の改修・更新に必要となる費用
              </div>
            </v-row>
            <v-row class="my-2 mx-3">
              <v-img :src="full_cost" max-width="90%"></v-img>
            </v-row>
            <v-row class="my-2 mx-3">
              <h2 class="primary--text">水道料金体系</h2>
            </v-row>
            <v-row class="my-2 mx-3">
              <div class="my-2">
                水道料金の体系は大きく分けて<strong>「用途別」</strong>と<strong>「口径別」</strong>に分けられます。<br />
                一般的に「基本料金」と「従量料金」で構成される「二部料金制」が採用されています。<br />
              </div>
              <div class="my-2">
                <strong>基本料金：固定的にかかる経費</strong><br />
                <strong>従量料金：使用した水量に応じて負担する経費</strong
                ><br />
              </div>
            </v-row>
            <v-row class="my-2 mx-3">
              <v-img :src="charge_system" max-width="50%"></v-img>
            </v-row>
            <v-row class="my-2 mx-3">
              <h3>全国の料金体系別の割合 <br /></h3>
            </v-row>
            <v-row class="my-2 mx-3">
              <div>出典：水道料金表（日本水道協会）<br /></div>
            </v-row>
            <v-row class="my-2">
              <v-col cols="12" md="6">
                <table
                  border="1"
                  style="border-collapse: collapse"
                  bgcolor="#FFFFFF"
                >
                  <tr>
                    <td valign="bottom"></td>
                    <td valign="bottom">区分</td>
                    <td valign="bottom">基本料金（準備料金）</td>
                    <td valign="bottom">事業体数</td>
                    <td valign="bottom">比率（%）</td>
                    <td valign="bottom">小計</td>
                  </tr>
                  <tr bgcolor="#BDD7EE">
                    <td valign="bottom"></td>
                    <td rowspan="3" align="center">用途別</td>
                    <td valign="bottom">用途別基本料金<br />基本水量あり</td>
                    <td align="right" valign="bottom">367</td>
                    <td align="right" valign="bottom">29.1</td>
                    <td rowspan="3" align="right" valign="bottom">380</td>
                  </tr>
                  <tr bgcolor="#BDD7EE">
                    <td valign="bottom"></td>
                    <td valign="bottom">単一基本料金<br />基本水量あり</td>
                    <td align="right" valign="bottom">12</td>
                    <td align="right" valign="bottom">1.0</td>
                  </tr>
                  <tr bgcolor="#BDD7EE">
                    <td valign="bottom"></td>
                    <td valign="bottom">単一基本料金<br />基本水量なし</td>
                    <td align="right" valign="bottom">1</td>
                    <td align="right" valign="bottom">0.1</td>
                  </tr>
                  <tr bgcolor="#F8CBAD">
                    <td valign="bottom"></td>
                    <td rowspan="2" align="center">口径別</td>
                    <td valign="bottom">基本水量無し<br />基本料金</td>
                    <td align="right" valign="bottom">323</td>
                    <td align="right" valign="bottom">25.6</td>
                    <td rowspan="2" align="right" valign="bottom">752</td>
                  </tr>
                  <tr bgcolor="#F8CBAD">
                    <td valign="bottom"></td>
                    <td valign="bottom">基本水量付<br />基本料金</td>
                    <td align="right" valign="bottom">429</td>
                    <td align="right" valign="bottom">34.0</td>
                  </tr>
                  <tr bgcolor="#DBDBDB">
                    <td valign="bottom"></td>
                    <td rowspan="3" align="center">その他</td>
                    <td valign="bottom">基本水量付<br />単一基本料金</td>
                    <td align="right" valign="bottom">116</td>
                    <td align="right" valign="bottom">9.2</td>
                    <td rowspan="3" align="right" valign="bottom">129</td>
                  </tr>
                  <tr bgcolor="#DBDBDB">
                    <td valign="bottom"></td>
                    <td valign="bottom">基本水量無し<br />単一基本料金</td>
                    <td align="right" valign="bottom">13</td>
                    <td align="right" valign="bottom">1.0</td>
                  </tr>
                  <tr bgcolor="#DBDBDB">
                    <td valign="bottom"></td>
                    <td valign="bottom">基本水量無し<br />基本料金なし</td>
                    <td align="right" valign="bottom">0</td>
                    <td align="right" valign="bottom">0.0</td>
                  </tr>
                  <tr>
                    <td valign="bottom"></td>
                    <td colspan="2" valign="bottom">合計</td>
                    <td align="right" valign="bottom">1261</td>
                    <td align="right" valign="bottom">100</td>
                    <td align="right" valign="bottom">1261</td>
                  </tr>
                </table>
              </v-col>
              <v-col cols="12" md="6">
                <v-img :src="ratio_system" max-width="90%"></v-img>
              </v-col>
            </v-row>
            <v-row class="my-2 mx-3 mt-10">
              <h3>全国の料金体系別の推移 <br /></h3>
            </v-row>
            <v-row class="my-2 mx-3">
              <table
                border="1"
                style="border-collapse: collapse"
                bgcolor="#FFFFFF"
              >
                <tr>
                  <td colspan="2" rowspan="2" align="center">区分</td>
                  <td rowspan="2" width="60" align="center">S40</td>
                  <td rowspan="2" width="60" align="center">S60</td>
                  <td rowspan="2" width="60" align="center">H17</td>
                  <td rowspan="2" width="60" align="center">H21</td>
                  <td rowspan="2" width="60" align="center">H25</td>
                  <td rowspan="2" width="60" align="center">H29</td>
                  <td rowspan="2" width="60" align="center">R3</td>
                </tr>
                <tr></tr>
                <tr bgcolor="#BDD7EE">
                  <td rowspan="2" width="70" align="center">用途別</td>
                  <td width="80" align="center">事業体数</td>
                  <td align="right">1,095</td>
                  <td align="right">868</td>
                  <td align="right">613</td>
                  <td align="right">471</td>
                  <td align="right">431</td>
                  <td align="right">404</td>
                  <td align="right">380</td>
                </tr>
                <tr bgcolor="#BDD7EE">
                  <td align="center">割合</td>
                  <td align="right">99.0%</td>
                  <td align="right">47.1%</td>
                  <td align="right">38.7%</td>
                  <td align="right">35.8%</td>
                  <td align="right">33.7%</td>
                  <td align="right">31.8%</td>
                  <td align="right">30.1%</td>
                </tr>
                <tr bgcolor="#F8CBAD">
                  <td rowspan="2" align="center">口径別</td>
                  <td align="center">事業体数</td>
                  <td align="right">11</td>
                  <td align="right">705</td>
                  <td align="right">783</td>
                  <td align="right">697</td>
                  <td align="right">708</td>
                  <td align="right">725</td>
                  <td align="right">752</td>
                </tr>
                <tr bgcolor="#F8CBAD">
                  <td align="center">割合</td>
                  <td align="right">1.0%</td>
                  <td align="right">38.3%</td>
                  <td align="right">49.4%</td>
                  <td align="right">53.0%</td>
                  <td align="right">55.4%</td>
                  <td align="right">57.1%</td>
                  <td align="right">59.6%</td>
                </tr>
                <tr bgcolor="#DBDBDB">
                  <td rowspan="2" align="center">その他</td>
                  <td align="center">事業体数</td>
                  <td align="right">0</td>
                  <td align="right">270</td>
                  <td align="right">190</td>
                  <td align="right">148</td>
                  <td align="right">140</td>
                  <td align="right">140</td>
                  <td align="right">129</td>
                </tr>
                <tr bgcolor="#DBDBDB">
                  <td align="center">割合</td>
                  <td align="right">0.0%</td>
                  <td align="right">14.7%</td>
                  <td align="right">12.0%</td>
                  <td align="right">11.2%</td>
                  <td align="right">10.9%</td>
                  <td align="right">11.0%</td>
                  <td align="right">10.2%</td>
                </tr>
                <tr>
                  <td rowspan="2" align="center">合計</td>
                  <td align="center">事業体数</td>
                  <td align="right">1,106</td>
                  <td align="right">1,843</td>
                  <td align="right">1,586</td>
                  <td align="right">1,316</td>
                  <td align="right">1,279</td>
                  <td align="right">1,269</td>
                  <td align="right">1,261</td>
                </tr>
                <tr>
                  <td align="center">割合</td>
                  <td align="right">100.0%</td>
                  <td align="right">100.0%</td>
                  <td align="right">100.0%</td>
                  <td align="right">100.0%</td>
                  <td align="right">100.0%</td>
                  <td align="right">100.0%</td>
                  <td align="right">100.0%</td>
                </tr>
              </table>
            </v-row>
            <v-row id="variant" class="my-2 mx-3">
              <v-img :src="change_graph" max-width="70%"></v-img>
            </v-row>
            <v-row class="my-2 mx-3">
              <div>口径別の割合が増えてきていることがわかりますね。 <br /></div>
            </v-row>

            <v-divider></v-divider>
            <v-row class="my-2">
              <v-col cols="12" md="5">
                <h1>口径と使用水量</h1>
              </v-col>
            </v-row>
            <v-row class="my-2 mx-3">
              <div>
                これまでの説明からもわかるように、日本の水道料金のほとんどは、
                <b>「使用量」</b>と<b>「口径」</b>で決まります。<br />
                では、「口径」とは一体何なのでしょうか。
              </div>
            </v-row>
            <v-row class="my-2 mx-2">
              <h2 class="primary--text">口径について</h2>
            </v-row>
            <v-row class="mb-1 mt-2 mx-3">
              <h3>口径とは？ <br /></h3>
            </v-row>
            <v-row class="mt-1 mb-2 mx-4">
              <div>
                口径とは、水を供給するための水道管の<b>太さ(直径)</b>のことです。
                地下水は口径が約150mmほどの大きさの水道管を流れていき、
                そこから家庭に水を供給するために細い口径の水道管へと流れます。
                家庭用水道水では主に、<b>13mm</b>、<b>20mm</b>の口径が用いられます。
                口径の太さが変わると、何が変わるのでしょうか。
              </div>
            </v-row>
            <v-row class="mb-1 mt-4 mx-3">
              <h3>口径が変わると？ <br /></h3>
            </v-row>
            <v-row class="mt-1 mb-2 mx-4">
              <div>
                口径が変わると<b>「一度に流すことができる水の量」</b>が変わります。
                複数の蛇口で水を同時に流す場合、口径が小さいとスムーズに水が流れなくなります。
                口径が20mmの場合、13mmと比較すると一度に出てくる水の量約2.4倍も多くなります。
                例えば、浴槽に水を溜めようとすると、口径20mmだと10分で溜まる場合、口径13mmだと25分近くかかってしまうという感じです。
                そうなると、『口径が大きい方が便利なのでは？』と思いますよね。
                しかしながら、口径が大きくなるほど水道料金は高くなっていきます。
                口径が13mmと20mmではどれくらい水道料金が異なるのかは、実際にデータをみて確認してみてください。
              </div>
            </v-row>
            <v-row class="mb-1 mt-4 mx-3">
              <h3>口径の決定 <br /></h3>
            </v-row>
            <v-row class="mt-1 mb-2 mx-4">
              <div>
                口径は建物によって決定します。そのため、アパートやマンションの集合住宅での口径は勝手に変更することはできません。
                そもそも、口径を変えようとすると工事を実施しなければならないため、賃貸住宅では基本的に口径の変更はできません。
                集合住宅の場合、親メーターと子メーターがあり、親メーターの口径は大きく子メーターの口径は小さくなっています。
                しかし、子メーターがない場合など親メーターで水道料金が計算されている場合があります。
                集合住宅に住む場合は、水道料金がどの口径で計算されているか確認する必要がありますね。<br /><br />
                新築で家を建てる場合は、大方の場合で工事業者が設計を行い口径をどの大きさにするか提案してくれます。
                もともと設置されてる口径と異なる口径の水道管を設置する場合は工事をする必要があるため別途料金が発生します。
                工事業者の提案を受けるのが確実ですが、自分たちでも考えてどうするのか決めることも大切です。
              </div>
            </v-row>
            <v-row class="my-2 mx-2">
              <h2 class="primary--text">使用水量について</h2>
            </v-row>
            <v-row class="mt-1 mb-2 mx-4">
              <div>
                皆さんは毎月どれくらい家庭で水を使用しているか把握していますか？
                <a
                  href="https://www.waterworks.metro.tokyo.lg.jp/kurashi/shiyou/jouzu.html"
                  target="_blank"
                  >東京都水道局の調査(令和2年)
                </a>
                では、世帯人数による水道使用量の平均は以下のような結果でした。
              </div>
            </v-row>
            <v-col cols="8" md="4">
              <v-row class="my-2 mx-3 box1">
                <ul>
                  <li>1人世帯：8.1㎥</li>
                  <li>2人世帯：14.9㎥</li>
                  <li>3人世帯：19.9㎥</li>
                  <li>4人世帯：23.1㎥</li>
                  <li>5人世帯：27.8㎥</li>
                  <li>6人以上世帯：34.1㎥</li>
                </ul>
              </v-row>
            </v-col>
            <v-row class="mt-1 mb-1 mx-4">
              <div>
                皆さんの毎月の使用量は平均と比較してどうでしょうか？
                本サイトで水道料金を確認する際は平均の使用量や実際の自分の使用量などを参考に見てみてください。<br /><br />
              </div>
            </v-row>
            <v-row id="data" class="mt-2 mb-2 mx-4">
              <div>
                本サイトでは、口径が「13mm」と「20mm」の場合と、水道料金が「10㎥」と「20㎥」の場合の水道料金データを表示しています。
                (基本料金と超過料金に関しては口径「13mm」のみを使用)
              </div>
            </v-row>
            <v-divider></v-divider>
            <v-row class="my-2">
              <v-col cols="12" md="5">
                <h1>水道料金データの見方</h1>
              </v-col>
            </v-row>
            <v-row class="my-2 mx-3">
              <div>
                本サイトで調べられる水道料金データには、次のようなものがあります。<br />
              </div>
            </v-row>
            <v-row class="my-2 mx-3 box2">
              <ul>
                <li><strong>日本全体の水道料金データ</strong></li>
                <ol>
                  <li>都道府県ごとの平均水道料金ランキング</li>
                  <li>平均水道料金マップ</li>
                  <li>事業体(市町村)の水道料金表</li>
                  <li>全国の事業体の基本料金と超過料金</li>
                  <li>水道料金比較シミュレーター</li>
                </ol>
                <li><strong>各都道府県ごとの水道料金データ</strong></li>
                <ol>
                  <li>都道府県内での水道料金ランキング</li>
                  <li>各事業体の水道料金グラフ</li>
                  <li>都道府県内の基本料金と超過料金表</li>
                  <li>水道料金計算シミュレータ</li>
                </ol>
              </ul>
            </v-row>
            <v-row class="my-2 mx-3">
              <div>
                本サイトでのデータの見方は以下の画像を参考にしてみてください。<br />
              </div>
            </v-row>
            <v-row justify="center">
              <v-icon color="#0E2997">mdi-circle</v-icon>
              <h2><font color="#0E2997">日本全体の水道料金データ</font></h2>
              <v-col cols="12">
                <v-img
                  :src="outlook_japan_pc_src"
                  class="hidden-sm-and-down"
                ></v-img>
                <v-img
                  :src="outlook_japan_sp_src"
                  class="hidden-md-and-up"
                ></v-img>
              </v-col>
            </v-row>
            <v-row class="mx-3 mb-5" justify="center">
              <div>
                <v-btn
                  x-large
                  color="#0E2997"
                  dark
                  width="100%"
                  style="text-transform: none"
                  @click="moveData()"
                >
                  <v-icon>mdi-chevron-right</v-icon>
                  <strong>&nbsp;日本全体の水道料金データを見てみよう！</strong>
                </v-btn>
              </div>
            </v-row>
            <v-row class="mt-10" justify="center">
              <v-icon color="#0E2997">mdi-circle</v-icon>
              <h2><font color="#0E2997">都道府県ごとの詳細データ</font></h2>
              <v-col cols="12">
                <v-img
                  :src="outlook_pref_pc"
                  class="hidden-sm-and-down"
                ></v-img>
                <v-img :src="outlook_pref_sp" class="hidden-md-and-up"></v-img>
              </v-col>
            </v-row>
            <v-row class="mx-3 mb-5" justify="center">
              <div>
                <v-btn
                  x-large
                  color="#0E2997"
                  dark
                  width="100%"
                  style="text-transform: none"
                  @click="moveDataPref()"
                >
                  <v-icon>mdi-chevron-right</v-icon>
                  <strong
                    >&nbsp;都道府県ごとの水道料金データを見てみよう！</strong
                  >
                </v-btn>
              </div>
            </v-row>
            <v-row class="my-3 mx-3">
              <div>
                <br />
                ※本サイトで使用する水道料金データは、
                <a
                  href="https://www.soumu.go.jp/main_sosiki/c-zaisei/kouei_kessan.html"
                  target="_blank"
                >
                  地方公営企業決算状況調査（通称：決算統計）
                </a>
                によって2021年に収集されたデータ を利用しています。<br /><br />
              </div>
            </v-row>
          </v-col>
        </v-row>
      </section>
    </v-container>
  </div>
</template>

<script>
import BreadCrumb from '~/components/atoms/BreadCrumb.vue'

export default {
  name: 'ChargeHome',
  components: {
    BreadCrumb,
  },
  data() {
    return {
      trandition_charge_system: require('@/assets/img/charge_intro/Charge_system_trandition.png'),
      rate_charge_system: require('@/assets/img/charge_intro/Water_rate_system_classification_table.png'),
      full_cost: require('@/assets/img/charge_intro/full_cost.png'),
      charge_system: require('@/assets/img/charge_intro/charge_system.png'),
      change_graph: require('@/assets/img/charge_intro/ratio_change_graph.png'),
      ratio_system: require('@/assets/img/charge_intro/ratio_system.png'),
      outlook_japan_pc_src: require('@/assets/img/outlook_charge/japan_pc.png'),
      outlook_japan_sp_src: require('@/assets/img/outlook_charge/japan_sp.png'),
      outlook_pref_pc: require('@/assets/img/outlook_charge/pref_pc.png'),
      outlook_pref_sp: require('@/assets/img/outlook_charge/pref_sp.png'),
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
          name: '水道料金',
        },
      ]
    },
  },
  methods: {
    moveData() {
      this.$router.push('/charge/data/')
    },
    moveDataPref() {
      this.$router.push('/charge/data/select_pref')
    },
  },
}
</script>

<style scoped>
.c-p {
  cursor: pointer;
}

.charge-intro {
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

.box2 ul {
  color: #0e2997;
  border: dashed 2px #668ad8;
  background: #f1f8ff;
  padding: 0.5em 0.5em 0.5em 2em;
  width: 110%;
}

.box2 ul li {
  line-height: 1.5;
  padding: 0.5em 0;
}

.box1 {
  padding: 0.5em 1em;
  margin: 0.5em 0;
  font-weight: bold;
  border: solid 3px #000;
}

.box1 p {
  margin: 0;
  padding: 0;
}
</style>