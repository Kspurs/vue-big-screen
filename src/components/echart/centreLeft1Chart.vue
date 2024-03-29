<template>
  <div>
    <div id="centreLeft1Chart" style="width:260px; height: 350px;"></div>
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
        document.getElementById("centreLeft1Chart")
      );
      //  ----------------------------------------------------------------
     let option = {
      tooltip: {
        trigger: 'item',
        triggerOn: 'mousemove'
      },
  series: {
    type: 'sankey',
    layout: 'none',
    emphasis: {
      focus: 'adjacency'
    },
    label: {
      show: true,
      color: '#fff'
    },
    data: [
      {
        name: '10.123.123.23'
      },
      {
        name: '10.123.123.25'
      },
      {
        name: '10.123.123.24'
      },
      {
        name: 'DNS'
      },
      {
        name: 'HTTP'
      },
      {
        name: '10.123.123.28'
      }
    ],
    links: [
      {
        source: '10.123.123.23',
        target: 'HTTP',
        value: 5
      },
      {
        source: '10.123.123.25',
        target: 'HTTP',
        value: 3
      },
      {
        source: '10.123.123.23',
        target: 'DNS',
        value: 8
      },
      {
        source: '10.123.123.23',
        target: '10.123.123.24',
        value: 3
      },
      {
        source: 'HTTP',
        target: '10.123.123.24',
        value: 1
      },
      {
        source: 'b1',
        target: 'c',
        value: 2
      }
    ]
  }
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
</style>