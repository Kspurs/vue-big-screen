<template>
  <div>
    <div id="centreRight2Chart1" style="width:350px; height: 190px;">123</div>
  </div>
</template>

<script>
const echarts = require("echarts");
export default {
  data() {
    return {};
  },
  mounted() {
    this.drawPie();
  },
  methods: {
    drawPie(sidebar) {
      // 基于准备好的dom，初始化echarts实例
      let myChartPieLeft = echarts.init(
        document.getElementById("centreRight2Chart1"),null,{width:"350px",height:"190px"}
      );
      //  ----------------------------------------------------------------
      // Schema:
      // date,AQIindex,PM2.5,PM10,CO,NO2,SO2
      let option = {
          title:{
              text:"包数变化",
              textStyle:{
                  color:"rgba(255,255,255,.8)",
                  fontSize:14
              },
          },
  tooltip: {
    trigger: 'axis'
  },
  grid: {
    left: '3%',
    right: '4%',
    bottom: '3%',
    containLabel: true
  },
  xAxis: {
    type: 'category',
    boundaryGap: false,
    data: ['5', '10', '15', '20', '25', '30'],
    axisLabel: {
            color: "rgba(255,255,255,.8)",
            fontSize: 12
          },
  },
  yAxis: {
    type: 'value',
    axisLabel: {
            color: "rgba(255,255,255,.8)",
            fontSize: 12
}, 
  },
  series: [
    {
      name: 'UDP',
      type: 'line',
      stack: 'Total',
      data: [120, 132, 101, 134, 90, 230]
    },
    {
      name: 'HTTP',
      type: 'line',
      stack: 'Total',
      data: [220, 182, 191, 234, 290, 330]
    },
    {
      name: 'TCP',
      type: 'line',
      stack: 'Total',
      data: [150, 232, 201, 154, 190, 330]
    },
    {
      name: 'DNS',
      type: 'line',
      stack: 'Total',
      data: [320, 332, 301, 334, 390, 330]
    },
  ]
};
      myChartPieLeft.setOption(option);
      // -----------------------------------------------------------------
      // 响应式变化
      window.addEventListener("resize", () => myChartPieLeft.resize(), false);
      //侧边栏变化
      if (sidebar) {
        myChartPieLeft.resize();
      }
    }
  },
  destroyed() {
    window.onresize = null;
  }
};
</script>

<style lang="scss" scoped>
#centreRight2Chart1{
  margin: 0 auto;
}
</style>