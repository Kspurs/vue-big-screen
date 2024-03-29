<template>
  <div style="height: 100%;">
    <div id="centerChart1" style="height:230px;width: 289px;padding-left: 5%;"></div>
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
    drawPie() {
      // 基于准备好的dom，初始化echarts实例
      let myChartPieLeft = echarts.init(
        document.getElementById("centerChart1"),null,{width:"270px",height:"170px"}
      );
      //  ----------------------------------------------------------------

      let option = {
        tooltip: {
          trigger: 'item'
        },
        series: [
          {
            type: "pie",
            hoverAnimation: true,
            color: ["#00bcd44a","#00bcd4","#ff9800","#ff98004a"],
            tooltip: {
                formatter:"{b}:{c}字节"
            },
            label: {
              show: true,
            },
            data: [
              {
                value: 30000,
                name:"HTTP\n"
              },
              {
                value: 20000,
                name:"TCP\n"
              },
              {
                value: 10000,
                name:"UDP\n"
              },
              {
                value: 5000,
                name:"DNS\n"
              }
            ]
          }
        ]
      };
      myChartPieLeft.setOption(option);
      // -----------------------------------------------------------------
      // 响应式变化
      window.addEventListener("resize", () => myChartPieLeft.resize(), false);
    }
  },
  destroyed() {
    window.onresize = null;
  }
};
</script>

<style lang="scss" scoped>
</style>