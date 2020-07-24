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
      name: "PerEc",
      'v-chart': ECharts
    },
    mounted: function () {
      var _this = this;
      getRequest("/article/data").then(resp=> {
        if (resp.status == 200) {
          // _this.$refs.dschart.options.xAxis.data = resp.data.categories;
          _this.$refs.dschart.options.series[0].data = resp.data.ds;
          // _this.$refs.dschart.options.series[1].data = resp.data.ds2;
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
          backgroundColor: '#07509A',
           title : {
            text: '信息情报',
            subtext: '',
            textStyle: {
              color: '#fff'
            },
          x:'center'
        },
          // toolbox: {
          //    iconStyle:{
          //           normal:{
          //             color:'white',//设置颜色
          //           }
          //       },
            
          //   show: true,
          //   feature: {
          //     dataZoom: {
          //       yAxisIndex: 'none'
          //     },
          //     dataView: {
          //       readOnly: false
          //     },
          //     // magicType: {
          //     //   type: ['line', 'bar']
          //     // },
          //     restore: {},
          //     saveAsImage: {}
          //   }
          // },
          tooltip: {
            trigger: 'item',
            formatter: "{a} <br/>{b}: {c} ({d}%)"
          },
          legend: {
            data: []
          },
          // xAxis: {
          //   data: []
          // },
          // yAxis: {},

          series: [
          {
            name: 'pv',
            type: 'pie',

            showSymbol : true,
            symbolSize : 10,
            radius : '65%',
            center: ['50%', '60%'],
            avoidLabelOverlap: false,
            itemStyle: {
                emphasis: {
                    shadowBlur: 10,
                    shadowOffsetX: 0,
                    shadowColor: 'rgba(0, 0, 0, 0.5)'
                }
            },
            label: {
                normal: {
                    show: false,
                    position: 'center'
                },
                emphasis: {
                    show: true,
                    textStyle: {
                        fontSize: '30',
                        fontWeight: 'bold'
                    }
                }
            },
            label : {
　　　　        normal : {
    　　　　　　  formatter: '{d}%',
    　　　　　　  textStyle : {
    　　　　　　　　fontWeight : 'normal',
    　　　　　　　　fontSize : 25
    　　　　　　　}
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
