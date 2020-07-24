<template>
  <div class="echartsdiv" 
    style="display: flex;height: 100%;width: 100%;align-items: center;justify-content: center;">
    <v-chart ref="dschart" :options="polar" :judge-width="true" style="height: 250px;width: 100%"></v-chart>
  </div>
</template>

<style>
</style>
<script>
  import ECharts from 'vue-echarts'
  import echarts from 'echarts'
  import 'echarts/lib/chart/line'
  import 'echarts/lib/component/tooltip'

  import 'echarts/lib/component/polar'

  import 'echarts/lib/component/legend'
  import 'echarts/lib/component/title'
  import 'echarts/theme/dark'
  import 'echarts/lib/chart/bar'

  import {getRequest} from '../../http/api2.js'
  export default{
    components: {
      name: "PerEc",
      'v-chart': ECharts
    },
    mounted: function () {
      var _this = this;
      getRequest("/article/data").then(resp=> {
        if (resp.status == 200) {
          // _this.$refs.dschart.options.xAxis.data = resp.data.categories;
          _this.$refs.dschart.options.series[0].data = resp.data.ds;
          _this.$refs.dschart.options.series[1].data = resp.data.ds2;
        } else {
          _this.$message({type: 'error', message: '数据加载失败!'});
        }
      }, resp=> {
        _this.$message({type: 'error', message: '数据加载失败!'});
      });
    },
    methods: {},
    data: function () {
      return {
        polar: {
          title: {
            text: '重点人员分级安检及跟踪',
            subtext: '',
            textStyle: {
              color: '#fff'
            }
          },
          backgroundColor: '#0A5AAB',
          // toolbox: {
          //    iconStyle:{
          //       normal:{
          //       color:'white',//设置颜色
          //       }
          //     },
          //   show: true,
          //   feature: {
          //     dataZoom: {
          //       show: false,
          //       start: 0,
          //       end: 100
          //     },
          //     dataView: {
          //       readOnly: false
          //     },
          //     magicType: {
          //       type: ['line', 'bar']
          //     },
          //     restore: {},
          //     saveAsImage: {}
          //   }
          // },
          tooltip: {
            trigger: 'axis',
            axisPointer: {
              type: 'cross',
                  label: {
                    backgroundColor: '#283b56'
                  }
              }
          },
          legend: {
            data:['人数', '预测'],
            textStyle:{
                fontSize: 18,//字体大小
                color: '#ffffff'//字体颜色
            },
          },
          xAxis: [
          {
            type: 'category',
            boundaryGap: true,
            axisLabel: {
              show: true,
              textStyle: {
                color: '#ffffff'
              }
            },
            data: (function (){
                var now = new Date();
                var res = [];
                var len = 7;
                while (len--) {
                    res.unshift(now.toLocaleTimeString().replace(/^\D*/,''));
                    now = new Date(now - 2000);
                }
                return res;
            })()
          },
          {
            type: 'category',
            boundaryGap: true,
            axisLabel: {
              show: true,
              textStyle: {
                color: '#ffffff'
              }
            },
            data: (function (){
                var res = [];
                var len = 7;
                while (len--) {
                    res.push(7 - len - 0);
                }
                return res;
            })()
        }
    ],
          yAxis: [
            {
              type: 'value',
              scale: true,
              name: '',
              max: 50,
              min: 0,
              boundaryGap: [0.2, 0.2],
              axisLabel: {
                show: true,
                textStyle: {
                  color: '#fff'
                }
              }
            },
            {
              type: 'value',
              scale: true,
              name: '',
              max: 50,
              min: 0,
              boundaryGap: [0.2, 0.2],
              axisLabel: {
                show: true,
                textStyle: {
                  color: '#ffffff'
                }
              }
            }
          ],

          series: [
          {
            name:'预测',
            type:'bar',
            // barMaxWidth: 15,
            itemStyle: {
                normal: {
                    color: new echarts.graphic.LinearGradient(
                        0, 0, 0, 1,
                        [
                            // {offset: 0, color: '#83bff6'},
                            // {offset: 0.5, color: '#67C23A'},
                            {offset: 1, color: 'red'}
                        ]
                    )
                },
                // emphasis: {
                //     color: new echarts.graphic.LinearGradient(
                //         0, 0, 0, 1,
                //         [
                //             {offset: 0, color: '#2378f7'},
                //             {offset: 0.7, color: '#2378f7'},
                //             {offset: 1, color: '#83bff6'}
                //         ]
                //     )
                // }
            },  
            data: [],
            
          },

          {
            name: '人数',
            type: 'line',
            showSymbol : true,
            symbolSize : 10,
            itemStyle: {
              normal: { 
                lineStyle: {
                  width:5, //调整 线条的宽度  
                  color : 'green', //线条颜色  
                }
              }
            },
            data: [], 
          }
          ],
          animationDuration: 3000
        }
      }
    }
  }
</script>
