<template>
 <div>
      <div ref="myChart" :style="{width:cwidth+'px', height:cheight+'px'}"></div>
     <!--  <div ref="myChart" :style="{width:'300px', height:'300px'}"></div> -->
 </div>
</template>

<script>
export default {
  name: "echarts1",
  data() {
    return {
      cwidth: 0,
      cheight: 0
    };
  },
  mounted() {
       var that = this;
    that.cwidth = document.documentElement.clientWidth/3;
   that.cheight = document.documentElement.clientHeight/3;
    window.onresize = function() {
      that.cwidth = document.documentElement.clientWidth/3;
      that.cheight =document.documentElement.clientHeight/3;
  
    };
    console.log(that.cwidth);
    console.log(that.cheight);
   that.$nextTick(function() {
            // DOM 更新了
           that.drawLine()
        })
  },
  methods: {

    drawLine() {
      // 基于准备好的dom，初始化echarts实例
      let myChart = this.$echarts.init(this.$refs.myChart);
      // 绘制图表
      myChart.setOption({
        title: { text: "在Vue中使用echarts" },
        tooltip: {},
        xAxis: {
          data: ["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"]
        },
        yAxis: {},
        series: [
          {
            name: "销量",
            type: "bar",
            data: [5, 20, 36, 10, 10, 20]
          }
        ]
      });
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
