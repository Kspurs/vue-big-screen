<template>
  <div id="centreLeft1">
    <div class="bg-color-black">
      <div class="d-flex pt-2 pl-2">
        <span style="color:#5cd9e8">
          <icon name="chart-bar"></icon>
        </span>
        <div class="d-flex">
          <span class="fs-xl text mx-2">流量关联情况</span>
          <dv-decoration-3 style="width:100px;height:20px; position:relative;top:-3px;" />
        </div>
      </div>
      <div class="d-flex jc-center">
        <centreLeft1Chart />
      </div>
      <!-- 4个主要的数据 -->
    </div>
  </div>
</template>

<script>
import centreLeft1Chart from "@/components/echart/centreLeft1Chart";
export default {
  data() {
    return {
      config: {
        lineWidth: 30,
        activeRadius: "80%",
        radius: "75%",
        activeTimeGap: 2000,
        data: [
          {
            name: "周口",
            value: 55
          },
          {
            name: "南阳",
            value: 120
          },
          {
            name: "西峡",
            value: 78
          },
          {
            name: "驻马店",
            value: 66
          },
          {
            name: "新乡",
            value: 80
          }
        ]
      },
      numberData: [
        {
          number: {
            number: [15],
            toFixed: 1,
            content: "{nt}"
          },
          text: "今日构建总量"
        },
        {
          number: {
            number: [1144],
            toFixed: 1,
            content: "{nt}"
          },
          text: "总共完成数量"
        },
        {
          number: {
            number: [361],
            toFixed: 1,
            content: "{nt}"
          },
          text: "正在编译数量"
        },
        {
          number: {
            number: [157],
            toFixed: 1,
            content: "{nt}"
          },
          text: "未通过数量"
        }
      ]
    };
  },
  components: {
    centreLeft1Chart
  },
  mounted() {
    this.changeTiming();
  },
  methods: {
    changeTiming() {
      setInterval(() => {
        this.changeNumber();
      }, 3000);
    },
    changeNumber() {
      this.numberData.forEach((item, index) => {
        item.number.number[0] += ++index;
        item.number = { ...item.number };
      });
    }
  }
};
</script>

<style lang="scss">
#centreLeft1 {
  padding: 1rem;
  height: 450px;
  min-width: 350px;
  border-radius: 5px;
  .bg-color-black {
    height: 385px;
    border-radius: 10px;
  }
  .text {
    color: #c3cbde;
  }
  .chart-box {
    margin-top: 1rem;
    width: 200px;
    height: 250px;
    .active-ring-name {
      padding-top: 10px;
    }
  }

  .bottom-data {
    .item-box {
      float: right;
      position: relative;
      width: 50%;
      color: #d3d6dd;
      // 金币
      .coin {
        position: absolute;
        left: 0px;
        top: 17px;
        font-size: 2rem;
        color: #ffc107;
      }
      .colorYellow {
        color: yellowgreen;
      }
    }
  }
}
</style>