<template>
  <div id="centreRight2">
    <div class="bg-color-black">
      <div class="d-flex pt-2 pl-2">
        <span style="color:#5cd9e8">
          <icon name="align-left"></icon>
        </span>
        <span class="fs-xl text mx-2">流量包数变化</span>
      </div>
      <div class="d-flex jc-center body-box">
        <centreRight2Chart1></centreRight2Chart1>
        <centerRight2Chart2></centerRight2Chart2>
      </div>
    </div>
  </div>
</template>

<script>
import centreRight2Chart1 from "@/components/echart/centreRight2/centreRight2Chart1";
import centerRight2Chart2 from "../components/echart/centreRight2/centerRight2Chart2.vue";
export default {
  data() {
    return {
      config: {
        data: [
          {
            name: "南阳",
            value: 167
          },
          {
            name: "周口",
            value: 67
          },
          {
            name: "漯河",
            value: 123
          },
          {
            name: "郑州",
            value: 55
          },
          {
            name: "西峡",
            value: 98
          }
        ]
      }
    };
  },
  components: { centreRight2Chart1,centerRight2Chart2},
  mounted() {},
  methods: {}
};
</script>

<style lang="scss">
#centreRight2 {
  padding: 5px;
  height: 400px;
  min-width: 300px;
  border-radius: 5px;
  .bg-color-black {
    padding: 5px;
    height: 405px;
    border-radius: 10px;
  }
  .text {
    color: #c3cbde;
  }
  .body-box {
    flex-direction: column;
    border-radius: 10px;
  }
}
</style>