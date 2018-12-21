<template>
  <div>
    <div id="mChart22" ref="two2"></div>
    <div>{{resdat}}</div>
  </div>
</template>
<script>
export default {
  name: "two2",
  data() {
    return {
      aadata: [],
      bbdata: [],
      ccdata: [],
      resdat:[]
    };
  },
  created() {
    var that = this;
    var aa = Math.random() * 1000;
    var cc = [];
    for (var i = 0; i < 100; i++) {
      that.aadata.push(aa);
      that.bbdata.push(i);
      cc.push(0);
    }
    cc.splice(cc.length - 1, 1, that.aadata[that.aadata.length - 1]);
    that.ccdata = cc;
  },
  mounted() {
    var that = this;
    that.$nextTick(function() {
      // DOM 更新了
      that.drawLine();
    });
  },
  methods: {
       
    drawLine() {
      var that = this;
      var myChart = this.$echarts.init(this.$refs.two2);
      var ydata = that.aadata;
      var xdata = that.bbdata;
      var zydata = that.ccdata;
   console.log(that.resdat)
      setInterval(function() {
        var that = this;
        /* arr = arr.slice(1, arr.length); */
        var b = Math.random() * 1500;
        ydata.push(b);
        xdata.push(b);
        zydata.splice(zydata.length - 1, 1, b);
        ydata.shift();
        xdata.shift();
        /*  ydata = ydata.slice(1, ydata.length);
        xdata = xdata.slice(1, xdata.length); */
        myChart.setOption({
          xAxis: {
            type: "category",
            boundaryGap: false,
            data: xdata
          },
          yAxis: {
            type: "value",
            max: 1500
          },
          series: [
            {
              data: ydata,
              type: "line",
              smooth: true,
              symbol: "none",
              lineStyle: {
                color: {
                  type: "linear",
                  /*   x: 0,
    y: 0,
    x2: 0,
    y2: 1, */
                  colorStops: [
                    {
                      offset: 0,
                      color: "#0eb92e" // 0% 处的颜色
                    },
                    {
                      offset: 0.8,
                      color: "#0eb92e" // 0% 处的颜色
                    },
                    {
                      offset: 1,
                      color: "#f0e242" // 100% 处的颜色
                    }
                  ],
                  opacity: 0.4,
                  globalCoord: false // 缺省为 false
                }
              }
            },
            {
              name: "最高气温",
              barWidth: 2,
              type: "bar",
              data: zydata,
              animation: false,
              markPoint: {
                animation: false,
                symbol: "emptyCircle",
                data: [{ type: "max" }],
                symbolSize: 16,
                itemStyle: {
                  normal: {
                    label: {
                      show: false
                    }
                  }
                }
              }
            }
          ]
        });
      }, 1000);
    }
  }
};
</script>
<style scoped>
#mChart22 {
  width: 100%;
  height: 400px;
}
</style>
