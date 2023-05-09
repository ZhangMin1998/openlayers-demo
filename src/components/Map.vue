<template>
  <div ref="map" class="map" id="map"></div>
</template>

<script>
import 'ol/ol.css'
import Map from 'ol/Map'
import View from 'ol/View'
import TileLayer from 'ol/layer/Tile'
import OSM from 'ol/source/OSM'

export default {
  name: 'Map',
  data() {
    return {
      map: null,
    }
  },
  mounted() {
    this.map = new Map({
      target: this.$refs.map,
      layers: [
        new TileLayer({
          source: new OSM()
        })
      ],
      // layers: [
      //   new TileLayer({
      //     source: new OSM({}),
      //   }),
      // ],
      // view: new View({
      //   center: [0, 0],
      //   zoom: 2
      // })
      view: new View({
        // 设置中心点，默认厦门，用于规划厦门市的未来发展
        center: [118.15075122802735, 24.482664909344276],
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
  height: 800px;
}
</style>
