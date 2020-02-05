<template>
  <div id="app">
    <div id="header">
      <h1>珠海新冠状病毒感染确诊热力图</h1>
      <p>所有数据来源于 <a target="_blank" href="https://mp.weixin.qq.com/s/KG8arbEJDtwduYzfG3sTfA">珠海发布</a> ，仅供参考</p>
    </div>
    <div id="container"></div>
  </div>
</template>

<script>
import data from '@/assets/data'

export default {
  name: 'app',
  mounted () {
    const BMap = window.BMap
    const BMapLib = window.BMapLib
    const map = new BMap.Map('container')
    const heatmapOverlay = new BMapLib.HeatmapOverlay({ radius: 10 })
    map.centerAndZoom(new BMap.Point(data[0].lng, data[0].lat), 11)
    map.addOverlay(heatmapOverlay)
    heatmapOverlay.setDataSet({ data: data[0].data, max: data[0].max })
    heatmapOverlay.show()
  }
}
</script>

<style lang="less">
#app, #container {
  height: 100%;
}
#header {
  position: fixed;
  left: 0;
  right: 0;
  padding: 6px 0;
  text-align: center;
  background-color: #ffffff;
  z-index: 1;
  > h1 {
    font-size: 16px;
    color: #333;
  }
  > p {
    margin-top: 1px;
    font-size: 12px;
    color: #777;
    > a {
      color: #576b95;
    }
  }
}
</style>
