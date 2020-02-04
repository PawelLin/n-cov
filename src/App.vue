<template>
  <div id="app">
  </div>
</template>

<script>
import data from '@/assets/data'

export default {
  name: 'app',
  mounted () {
    const BMap = window.BMap
    const BMapLib = window.BMapLib
    const map = new BMap.Map('app')
    const heatmapOverlay = new BMapLib.HeatmapOverlay({ radius: 10 })
    map.centerAndZoom(new BMap.Point(data[0].lng, data[0].lat), 11)
    map.addOverlay(heatmapOverlay)
    heatmapOverlay.setDataSet({ data: data[0].data, max: data[0].max })
    heatmapOverlay.show()
  }
}
</script>

<style lang="less">
#app {
  height: 100%;
}
</style>
