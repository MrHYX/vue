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
          backgroundColor: '#0A5AAB',
          title: {
            text: '航站楼风险',
            subtext: '',
            textStyle: {
              color: '#fff'
            },
          },
          // toolbox: {
          //    iconStyle:{
          //       normal:{
          //       color:'white',//设置颜色
          //       }
          //     },
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
          tooltip: {
            trigger: 'axis'
          },
          legend: {
            data:['劫机','炸机'],
            textStyle:{
                fontSize: 18,//字体大小
                color: '#ffffff'//字体颜色
            },
          },
          xAxis: {
            type: 'category',
            boundaryGap: false,
            data: ['周一','周二','周三','周四','周五','周六','周日'],
            axisLabel: {
                show: true,
                textStyle: {
                    color: '#ffffff'
                }
            }
          },
          yAxis: {
            type: 'value',
            axisLabel: {
              formatter: '{value}%',
              show: true,
              textStyle: {
                color: '#ffffff'
              }
            }
          },

          series: [
          {
            name: '劫机',
            type: 'line',

            showSymbol : true,
            symbolSize : 10,
            itemStyle: {
              normal: { 
                lineStyle: {
                  width:5, //调整 线条的宽度  
                  color : 'red', //线条颜色   
                }
              }
            },  
            data: [],
            markPoint: {
                data: [
                    {type: 'max', name: ''},
                    {type: 'min', name: ''}
                ]
            },
            markLine: {
                data: [
                    {type: 'average', name: ''}
                ]
            }
          },

          {
            name: '炸机',
            type: 'line',
            showSymbol : true,
            symbolSize : 10,
            itemStyle: {
              normal: { 
                lineStyle: {
                  width:5, //调整 线条的宽度  
                  color : 'purple', //线条颜色  
                }
              }
            },
            data: [],
            markPoint: {
                data: [
                    {name: '周最低', value: -2, xAxis: 1, yAxis: -1.5}
                ]
            },
            markLine: {
                data: [
                    {type: 'average', name: ''},
                    [{
                        symbol: 'none',
                        x: '90%',
                        yAxis: 'max'
                    }, {
                        symbol: 'circle',
                        label: {
                            normal: {
                                position: 'start',
                                formatter: ''
                            }
                        },
                        type: 'max',
                        name: ''
                    }]
                ]
            }
          }
          ],
          animationDuration: 3000
        }
      }
    }
  }
</script>
