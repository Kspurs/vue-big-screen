<template>
  <div style="display: flex;">
    <div id="bottomRightChart1" style="width:900px;height:500px;"></div>
    <div id="bottomRightChart2" style="width:900px;height:500px;"></div>
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
      let barChartLeft = echarts.init(
        document.getElementById("bottomRightChart1")
      );
      let barChartRight = echarts.init(
        document.getElementById("bottomRightChart2")
      );
      //  ----------------------------------------------------------------
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
let option1 = {
  title: {
    text: '目的IP地址流量',
    textStyle: {
      color: "rgba(255,255,255,.8)",
      fontSize: 12
    }
  },
  tooltip: {
    trigger: 'axis',
    axisPointer: {
      type: 'shadow'
    }
  },
  legend: {
    show: true,
    left:'100px',
    selectedMode: false,
    textStyle: {
      color: "rgba(255,255,255,.8)",
      fontSize: 12
    },
  },
  grid,
  yAxis: {
    type: 'category',
    axisLabel: {
      color: "rgba(255,255,255,.8)",
      fontSize: 12,
      show:true
    },
    data: ['10.12.3.1', '10.12.3.1', '10.12.3.1', '10.12.3.1', '10.12.3.1', '10.12.3.1', '10.12.3.1']
  },
  xAxis: {
    axisLabel: {
      show:true,
      color: "rgba(255,255,255,.8)",
      fontSize: 12
    },
    type: 'value',
  },
  series
};
let option2= {
  title: {
    text: '源IP地址流量',
    textStyle: {
      color: "rgba(255,255,255,.8)",
      fontSize: 12
    }
  },
  tooltip: {
    trigger: 'axis',
    axisPointer: {
      type: 'shadow'
    }
  },
  grid,
  yAxis: {
    type: 'category',
    axisLabel: {
      color: "rgba(255,255,255,.8)",
      fontSize: 12,
      show:true
    },
    data: ['10.12.3.1', '10.12.3.1', '10.12.3.1', '10.12.3.1', '10.12.3.1', '10.12.3.1', '10.12.3.1']
  },
  xAxis: {
    axisLabel: {
      show:true,
      color: "rgba(255,255,255,.8)",
      fontSize: 12
    },
    type: 'value',
    
  },
  series
};
      barChartLeft.setOption(option1);
      barChartRight.setOption(option2);
      // -----------------------------------------------------------------
      // 响应式变化
      window.addEventListener("resize", () => barChartLeft.resize(), false);
    }
  },
  destroyed() {
    window.onresize = null;
  }
};
</script>

<style lang="scss" scoped>
</style>