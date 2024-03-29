<template>
  <div id="center">
    <div class="up">
      <div class="bg-color-black item" v-for="item in titleItem" :key="item.title">
        <p class="ml-3 colorBlue fw-b">{{item.title}}</p>
        <div>
          <dv-digital-flop :config="item.number" style="width:100%;height:30px;" />
        </div>
      </div>
    </div>
    <div class="down">
      <!-- <div class="ranking bg-color-black">
        <span style="color:#5cd9e8">
          <icon name="align-left"></icon>
        </span>
        <span class="fs-xl text mx-2 mb-1">年度负责人组件达标榜</span>
        <dv-scroll-ranking-board :config="ranking" style="height:220px" />
      </div> -->
      <div class="percent">
        <div class="item  bg-color-black">
          <span>应用流量占比</span>
          <centerChart1 />
        </div>
        <div class="item  bg-color-black">
          <span>应用包数占比</span>
          <centerChart2 />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import centerChart1 from "@/components/echart/center/centerChart1";
import centerChart2 from "@/components/echart/center/centerChart2";

export default {
  data() {
    return {
      titleItem: [
        {
          title: "总流量",
          number: {
            number: [2000000],
            toFixed: 0,
            content: "{nt}字节",
            textAlign: "center",
        }},
        {
          title: "总包数",
          number: {
            number: [100000],
            toFixed: 0,
            content: "{nt}",
            textAlign: "center"
          },
          textAlign: "center"
        },
        {
          title: "平均每分钟流量",
          number: {
            number: [60000],
            toFixed: 0,
            content: "{nt}字节",
            textAlign: "center"
          },
          textAlign: "center"
        },
        {
          title: "平均每分钟包数",
          number: {
            number: [3000],
            toFixed: 0,
            content: "{nt}",
            textAlign: "center"
          },
          textAlign: "center"
        },
        {
          title: "总目的IP地址数",
          number: {
            number: [106],
            toFixed: 0,
            content: "{nt}",
            textAlign: "center"
          },
          textAlign: "center"
        },
        {
          title: "总源IP地址数",
          number: {
            number: [100],
            toFixed: 0,
            content: "{nt}",
            textAlign: "center"
          },
          textAlign: "center"
        }
      ],
      ranking: {
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
          },
          {
            name: "新乡",
            value: 80
          },
          {
            name: "新乡",
            value: 80
          },
          {
            name: "新乡",
            value: 80
          }
        ],
        waitTime: 4000,
        carousel: "page",
        unit: "份"
      },
      water: {
        data: [24, 45],
        shape: 'roundRect',
        formatter:'{value}%',
        waveNum:3
      }
    };
  },
  components: {
    centerChart1,
    centerChart2
  }
};
</script>

<style lang="scss" scoped>
#center {
  display: flex;
  flex-direction: column;
  .up {
    width: 100%;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    .item {
      border-radius: 5px;
      padding-top: 1rem;
      margin-top: 0.5rem;
      width: 32%;
      height: 70px;
    }
  }
  .down {
    padding: 4px;
    padding-bottom: 0px;
    width: 100%;
    display: flex;
    height: 255px;
    justify-content: space-between;
    .bg-color-black {
      border-radius: 5px;
    }
    .ranking {
      padding: 10px;
      width: 59%;
    }
    .percent {
      width: 100%;
      display: flex;
      flex-wrap: wrap;
      .item {
        width: 50%;
        height: 100%; 
        span {
          margin-top: 7px;
          display: flex;
          justify-content: center;

        }
      }
      .water {
        width: 100%;
      }
    }
  }
}
</style>