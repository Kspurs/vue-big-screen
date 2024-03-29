<template>
  <div>
    <div id="centreLeft2Chart" style="width:500px; height: 370px;"></div>
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
        document.getElementById("centreLeft2Chart")
      );
      //  ----------------------------------------------------------------
      // There should not be negative values in rawData
const rawData = [
  [100, 302, 301, 334, 390, 330, 320],
  [320, 132, 101, 134, 90, 230, 210],
  [220, 182, 191, 234, 290, 330, 310],
  [150, 212, 201, 154, 190, 330, 410],
  [820, 832, 901, 934, 1290, 1330, 1320]
];
const totalData = [];
for (let i = 0; i < rawData[0].length; ++i) {
  let sum = 0;
  for (let j = 0; j < rawData.length; ++j) {
    sum += rawData[j][i];
  }
  totalData.push(sum);
}
const grid = {
  left: 100,
  right: 100,
  top: 50,
  bottom: 50
};
const series = [
  'HTTP',
  'TCP',
  'DNS',
  'FTP',
  'UDP'
].map((name, sid) => {
  return {
    name,
    type: 'bar',
    stack: 'total',
    barWidth: '60%',
    label: {
      show: false,
    },
    data: rawData[sid].map((d, did) =>
      totalData[did] <= 0 ? 0 : d 
    )
  };
});
let  option = {
  tooltip: {
    trigger: 'axis',
    axisPointer: {
      type: 'shadow'
    }
  },
  legend: {
    selectedMode: false,
    textStyle: {
      color: "rgba(255,255,255,.8)",
      fontSize: 12
    },
  },
  grid,
  yAxis: {
    type: 'value',
    axisLabel: {
      color: "rgba(255,255,255,.8)",
      fontSize: 12
    }
  },
  xAxis: {
    axisLabel: {
      show:false,
      color: "rgba(255,255,255,.8)",
      fontSize: 12
    },
    type: 'category',
    data: ['10.12.3.1-10.3.45.5', '10.12.3.1-10.3.45.5', '10.12.3.1-10.3.45.5', '10.12.3.1-10.3.45.5', '10.12.3.1-10.3.45.5', '10.12.3.1-10.3.45.5', '10.12.3.1-10.3.45.5']
  },
  series
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