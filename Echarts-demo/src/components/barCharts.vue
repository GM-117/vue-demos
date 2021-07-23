<template>
  <div>
    <h1>BarChart 根据 Echarts 组件创建条形图</h1>
    <div ref="barChart" style="width: 100%; height: 300px"></div>
  </div>
</template>

<script>
export default {
  props: {
    xDate: {
      type: Array,
      default: () => {
        return [];
      },
    },
  },
  data() {
    return {
      myChart: null,
      option: {},
    };
  },
  mounted() {
    this.initChart();
    window.addEventListener("resize", this.handleResize);
  },
  methods: {
    initChart() {
      this.myChart = this.$echarts.init(this.$refs.barChart);
      // console.log(this.myChart)
      this.option = {
        xAxis: {
          type: "category",
          // 从 props 组件外拿数据
          data: this.xDate,
        },
        yAxis: {
          type: "value",
        },
        series: [
          {
            data: [120, 200, 150, 80, 70, 110, 130],
            type: "bar",
            showBackground: true,
            backgroundStyle: {
              color: "rgba(180, 180, 180, 0.2)",
            },
          },
        ],
      };
      this.myChart && this.myChart.setOption(this.option);
    },
    handleResize() {
      this.myChart && this.myChart.resize();
    },
  },
};
</script>

<style>
</style>