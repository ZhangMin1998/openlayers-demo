<template>
  <div ref="map" class="map" id="map"></div>
</template>

<script>
// 'https://pgis.gatsd/arcgis/rest/services/sdsl_blue/MapServer'
import 'ol/ol.css'
import Map from 'ol/Map'
import View from 'ol/View'
import Layer from 'ol/layer'
import TileLayer from 'ol/layer/Tile'
import OSM from 'ol/source/OSM'
// import { XYZ } from 'ol/source'
import { XYZ, TileArcGISRest, ArcGISTiledMapServiceLayer } from 'ol/source'

export default {
  name: 'Map',
  data() {
    return {
      // map: null,
    }
  },
  mounted() {
    const map = new Map({
      target: this.$refs.map,
      layers: [
        new TileLayer({
          source: new TileArcGISRest({
            url: 'https://map.geoq.cn/ArcGIS/rest/services/ChinaOnlineCommunity/MapServer',   //   王海哥哥  等下你注释这行
            // url: 'https://map.geoq.cn/ArcGIS/rest/services/sdsl_blue/MapServer',           // 王海哥哥  等下你运行这行
          })
        })
      ],
      // layers: [
      //   //创建一个使用Open Street Map地图源的瓦片图层
      //   new TileLayer({
      //     source: new OSM()
      //   })
      // ],
      view: new View({
        // 设置中心点，默认厦门，用于规划厦门市的未来发展
        center: [114.15075122802735, 25.482664909344276],
        // center: ol.proj.fromLonLat([37.41, 8.82]),
        projection: 'EPSG:4326',
        // 设置缩放倍数
        zoom: 8,
        minZoom: 6,
        maxZoom: 20
      })
    })
  }
}
</script>

<style scoped>
.map {
  height: 900px;
  /* height: 100%; */
}
</style>
