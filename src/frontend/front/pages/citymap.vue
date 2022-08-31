<template>
  <div id="chartdiv"></div>
</template>

<script>
// import * as am4core from '@amcharts/amcharts4/core'
// import * as am4maps from '@amcharts/amcharts4/maps'
// 世界地図のgeodataを取得
// import am4geodataJapanLow from '@amcharts/amcharts4-geodata/japanHigh'
import japan from '@/assets/japan_geodata'

export default {
  name: 'IndexPage',
  // asyncData() {
  //   const japan_json = `@/assets/mockup_data/japan_data.json`
  //   return {
  //     japan_json,
  //   }
  // },
  mounted() {
    const { am4core, am4maps } = this.$am4core()

    const HeatmapColor = {
      max: '#51AA12',
      min: '#e4f1d9',
      hover: '#2D5E0A',
    }

    const map = am4core.create('chartdiv', am4maps.MapChart)
    map.geodata = japan
    map.projection = new am4maps.projections.Miller()
    const JapanSeries = map.series.push(new am4maps.MapPolygonSeries())
    JapanSeries.useGeodata = true
    // 日本地図ポリゴン設定
    const JapanPolygon = JapanSeries.mapPolygons.template
    // 日本地図ツールチップ
    JapanPolygon.tooltipText = '{name}: {value}'
    JapanPolygon.fill = am4core.color(HeatmapColor.hover)
    // 日本地図ホバー
    const JapanHs = JapanPolygon.states.create('hover')
    JapanHs.properties.fill = am4core.color(HeatmapColor.hover)
    // 日本地図ヒートマップ
    JapanSeries.heatRules.push({
      property: 'fill',
      target: JapanPolygon,
      min: am4core.color(HeatmapColor.min),
      max: am4core.color(HeatmapColor.max),
    })

    const JapanHeatLegend = map.createChild(am4maps.HeatLegend)
    JapanHeatLegend.series = JapanSeries
    JapanHeatLegend.align = 'right'
    JapanHeatLegend.height = am4core.percent(80)
    JapanHeatLegend.orientation = 'vertical'
    JapanHeatLegend.valign = 'middle'
    JapanHeatLegend.marginRight = am4core.percent(4)
    JapanHeatLegend.valueAxis.renderer.opposite = true
    JapanHeatLegend.valueAxis.renderer.dx = -25
    JapanHeatLegend.valueAxis.strictMinMax = false
    JapanHeatLegend.valueAxis.fontSize = 9
    JapanHeatLegend.valueAxis.logarithmic = false

    // 日本地図: 配送量データ読み込み
    JapanSeries.data = require('@/assets/mockup_data/japan_data.json')

    // 地方地図：読み込み・設定
    const CitySeries = map.series.push(new am4maps.MapPolygonSeries())
    CitySeries.useGeodata = true
    CitySeries.hide()
    // 市町村地図: ポリゴン設定
    const CityPolygon = CitySeries.mapPolygons.template

    // 市町村別地図: ツールチップ
    CityPolygon.tooltipText = '{name}: {value}'
    CityPolygon.fill = am4core.color(HeatmapColor.hover)

    // 市町村別地図: ホバー
    const CityHs = CityPolygon.states.create('hover')
    CityHs.properties.fill = am4core.color(HeatmapColor.hover)

    // 市町村別地図: ヒートマップ
    CitySeries.heatRules.push({
      property: 'fill',
      target: CityPolygon,
      min: am4core.color(HeatmapColor.min),
      max: am4core.color(HeatmapColor.max),
    })

    const CityHeatLegend = map.createChild(am4maps.HeatLegend)
    CityHeatLegend.series = CitySeries
    CityHeatLegend.align = 'right'
    CityHeatLegend.height = am4core.percent(80)
    CityHeatLegend.orientation = 'vertical'
    CityHeatLegend.valign = 'middle'
    CityHeatLegend.marginRight = am4core.percent(4)
    CityHeatLegend.valueAxis.renderer.opposite = true
    CityHeatLegend.valueAxis.renderer.dx = -25
    CityHeatLegend.valueAxis.strictMinMax = false
    CityHeatLegend.valueAxis.fontSize = 9
    CityHeatLegend.valueAxis.logarithmic = false
    CityHeatLegend.hide()

    // 市町村別地図: 市町村別地図が読み込みが終わったら日本全体地図を閉じて，市町村別地図だけを表示
    CitySeries.geodataSource.events.on('done', function (ev) {
      JapanSeries.hide()
      JapanHeatLegend.hide()
      CitySeries.show()
      CityHeatLegend.show()
    })

    // 市町村別地図: 地図・配送データの動的読み込みのためのイベントを日本地図側に設定
    JapanPolygon.events.on('hit', function (ev) {
      const PrefName = ev.target.dataItem.dataContext.name
      const VirtualLati = ev.target.dataItem.dataContext.virtual_lati
      const VirtualLong = ev.target.dataItem.dataContext.virtual_long

      if (VirtualLati !== undefined) {
        // console.log(virtual_lati);
        map.zoomToGeoPoint(
          {
            latitude: VirtualLati,
            longitude: VirtualLong,
          },
          20,
          true
        )
      } else {
        map.zoomToMapObject(ev.target)
      }
      // onoff_zoompan(false, 20);

      if (PrefName) {
        ev.target.isHover = false
        // 市町村別地図: 地図データ読み込み
        CitySeries.geodataSource.url = '@/assets/map_data/' + PrefName + '.json'
        CitySeries.geodataSource.load()

        // 市町村別地図: 数量データ読み込み
        CitySeries.dataSource.url = require('@/assets/mockup_data/' +
          PrefName +
          '.json')
        CitySeries.dataSource.load()

        // 市町村別地図: 数量データのデフォルト値を設定
        // https://www.amcharts.com/docs/v4/tutorials/manipulating-chart-data/
        CitySeries.events.on('beforedatavalidated', function (ev) {
          ev.target.data.forEach(
            (obj) => (obj.value = obj.value === undefined ? 0 : obj.value)
          )
        })

        // 市町村別地図: 数量データ読み込み時のエラーハンドリング
        CitySeries.dataSource.events.on('error', function (ev) {
          // デフォルトのエラーモーダルを閉じる
          map.modal.close()
          // 日本語のエラーを表示
          map.openModal(
            `エラー: ${PrefName}の詳細データが読み込めませんでした．`,
            'エラー'
          )
          // 以前のデータを削除
          CitySeries.data.length = 0
        })
        back.show()
      }
    })
    const back = map.createChild(am4core.ZoomOutButton)
    back.align = 'right'
    back.marginRight = am4core.percent(10)
    back.hide()
    back.events.on('hit', function (ev) {
      ResetMap()
    })

    function ResetMap() {
      // onoff_zoompan(true);
      JapanSeries.show()
      JapanHeatLegend.show()
      map.goHome(500)
      CitySeries.hide()
      CityHeatLegend.hide()
      back.hide()
    }
  },
  beforeDestroy() {
    if (this.map) {
      this.map.dispose()
    }
  },
}
</script>
<style scoped>
#chartdiv {
  width: 100%;
  height: 600px;
}
</style>