<template>
  <div class="echartsdiv" 
    style="display: flex;height: 100%;width: 100%;align-items: center;justify-content: center;">
    <v-chart ref="dschart" :options="polar" :judge-width="true" style="height:250px;width: 100%"></v-chart>
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
      name: "box333",
      'v-chart': ECharts
    },
    mounted: function () {
      var _this = this;
      getRequest("/article/data").then(resp=> {
        if (resp.status == 200) {
          _this.$refs.dschart.options.xAxis.data = resp.data.categories;
          _this.$refs.dschart.options.series[0].data = resp.data.ds;
          // _this.$refs.dschart.options.series[1].data = resp.data.ds2;
        } else {
          _this.$message({type: 'error', message: '数据加载失败!'});
        }
      }, resp=> {
        _this.$message({type: 'error', message: '数据加载失败!'});
      });
    },
    methods: {
      
    },
    data: function () {
      return {
        polar: {
          backgroundColor: '#fff',
          title: {
            text: '',
            subtext: '',
            textStyle: {
                color: '#07509Af'
            }
          },
          // toolbox: {
          //   iconStyle:{
          //     normal:{
          //       color:'white',//设置颜色
          //     }
          //   },
          //   show: true,
          //   feature: {
          //     dataZoom: {
          //       yAxisIndex: 'none'
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
          tooltip: {},
          legend: {
            data: ['风险指数'],
            textStyle: {
                color: '#07509A'
            }
          },
          xAxis: {
            data: [],
            offset: 20,
            axisLabel: {
            inside: true,
            textStyle: {
                color: '#fff'
            }
          },
          axisTick: {
            show: false
          },
          axisLine: {
            show: false
          },
          // z: 10
         },
          yAxis: {
            axisLine: {
                show: false
            },
            axisTick: {
                show: false
            },
            axisLabel: {
                formatter: '{value}%',
                show: true,
                textStyle: {
                    color: '#07509A'
                }
              }
          },
          dataZoom: [
            {
              type: 'inside'
            }
          ],
          series: [
          // { // For shadow
          //   type: 'bar',
          //   itemStyle: {
          //       normal: {color: 'rgba(0,0,0,0.05)'}
          //   },
          //   barGap:'-100%',
          //   barCategoryGap:'40%',
          //   data: [100,100,100,100,100,100,100],
          //   animation: false
          // },
          {
            name: '风险指数',
            type: 'bar',
            itemStyle: {
                normal: {
                    color: new echarts.graphic.LinearGradient(
                        0, 0, 0, 1,
                        [
                            {offset: 0, color: '#83bff6'},
                            {offset: 0.5, color: '#67C23A'},
                            {offset: 1, color: '#67C23A'}
                        ]
                    )
                },
                emphasis: {
                    color: new echarts.graphic.LinearGradient(
                        0, 0, 0, 1,
                        [
                            {offset: 0, color: '#2378f7'},
                            {offset: 0.7, color: '#2378f7'},
                            {offset: 1, color: '#83bff6'}
                        ]
                    )
                }
            }, 
            data: []
          },
          ],
          animationDuration: 3000
        }
      }
    }
  }
</script>
