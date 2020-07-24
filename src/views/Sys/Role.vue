<template>
    <div style="background-color: #909399;">
    <el-row :gutter="10">
      <el-col :span="8"><box11 class="grid-content bg-purple"></box11></el-col>
      <el-col :span="8"><box22 class="grid-content bg-purple"></box22></el-col>
      <el-col :span="8"><box33 class="grid-content bg-purple"></box33></el-col>
    </el-row>
    <el-row :gutter="10">
      <el-col :span="8"><box44 class="grid-content bg-purple"></box44></el-col>
      <el-col :span="8"><box55 class="grid-content bg-purple"></box55></el-col>
      <el-col :span="8"><box66 class="grid-content bg-purple"></box66></el-col>
    </el-row>
      
</div>
</template>

<script>
    import box11 from '../Echarts/box11.vue';
    import box22 from '../Echarts/box22.vue';
    import box33 from '../Echarts/box33.vue';
    import box44 from '../Echarts/box44.vue';
    import box55 from '../Echarts/box55.vue';
    import box66 from '../Echarts/box66.vue';
    import box77 from '../Echarts/box77.vue';
    import ECharts from 'vue-echarts'
  
    export default{
      components:{box11,box22,box33,box44,box55,box66,box77},
       data(){
         return {
            }   
       },
       methods: {
          
       },
       mounted() {
        
       },
      beforeDestroy() {
        
      },
    }
</script>
<style>
    .el-row {
    display: flex;
    margin-bottom: 10px;
    &:last-child {
      margin-bottom: 0;
    }
  }
  .el-col {
    display: flex;
    border-radius: 4px;
  }
  .bg-purple-dark {
    background: #99a9bf;
  }
  .bg-purple {
    background: #fff;

  }
  .bg-purple-light {
    background: #0A417A;
  }
  .grid-content {
    border-radius: 4px;
    min-height: 36px;
  }
  .row-bg {
    padding: 10px 0;
    
  }
  .box1 {
    height: 400px;
  }
  .box2 {
    height: 400px;
    background-color: #053363;
  }
  .box3 {
    box-sizing: border-box;
    height: 400px;
  }
  .box4 {
    box-sizing: border-box;
    height: 400px;
  }
  .box5 {
    box-sizing: border-box;
    height: 400px;
  }
  .box6 {
    box-sizing: border-box;
    height: 400px;
  }
  .box7 {
    height: 400px;
    box-sizing: border-box;
  }
</style>