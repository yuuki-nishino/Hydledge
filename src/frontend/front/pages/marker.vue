<template>
  <div id="chartdiv"></div>
</template>

<script>
// import * as am4core from '@amcharts/amcharts4/core'
// import * as am4maps from '@amcharts/amcharts4/maps'
// 世界地図のgeodataを取得
// import am4geodataJapanLow from '@amcharts/amcharts4-geodata/japanHigh'

export default {
  name: 'MarkerPage',
  mounted() {
    const { am4core, am4maps, am4geodataJapanLow } = this.$am4core()
    const map = am4core.create('chartdiv', am4maps.MapChart)
    map.geodata = am4geodataJapanLow
    map.projection = new am4maps.projections.Miller()
    const polygonSeries = map.series.push(new am4maps.MapPolygonSeries())
    polygonSeries.useGeodata = true

    polygonSeries.mapPolygons.template.events.on('hit', function (ev) {
      map.zoomToMapObject(ev.target)
    })

    const imageSeries = map.series.push(new am4maps.MapImageSeries())
    imageSeries.sequencedInterpolation = true

    const imageSeriesTemplate = imageSeries.mapImages.template

    // マーカーの形を定義(丸を指定)
    const circle = imageSeriesTemplate.createChild(am4core.Circle)
    // マーカーの色
    circle.fill = am4core.color('orange')
    // マーカーのサイズ
    circle.radius = 3
    // 枠線の色
    circle.stroke = am4core.color('red')
    // 枠線のサイズ
    circle.strokeWidth = 0
    // ツールチップに表示するテキスト dataのtextを表示できる
    circle.tooltipText = '{title}'

    // imageSeriesTemplateのlatitute,longitude(緯度経度)と配列の要素を紐付け
    imageSeriesTemplate.propertyFields.latitude = 'latitude'
    imageSeriesTemplate.propertyFields.longitude = 'longitude'

    imageSeries.data = [
      {
        title: 'Miyazaki',
        latitude: 31.9076761,
        longitude: 131.4202441,
      },
    ]
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