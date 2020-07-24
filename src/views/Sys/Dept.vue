<template>
    <div style="background-color: #fff;">
  <el-row :gutter="5">      
      <el-col :span="8"><box111 class="grid-content bg-purple"></box111></el-col>
      <span class="span"><img class="user-info" :src="imgUrl1" /></span>
      <el-col :span="8"><box222 class="grid-content bg-purple"></box222></el-col>
     
    </el-row>


    <el-row :gutter="5">      
      <el-col :span="8"><box333 class="grid-content bg-purple"></box333></el-col>
      <span class="span"><img class="user-info" :src="imgUrl2" /></span>
      <el-col :span="8"><box444 class="grid-content bg-purple"></box444></el-col>
     
    </el-row>

    <el-row :gutter="5">      
      <el-col :span="8"><box555 class="grid-content bg-purple"></box555></el-col>
      <span class="span"><img class="user-info" :src="imgUrl3" /></span>
      <el-col :span="8"><box666 class="grid-content bg-purple"></box666></el-col>
     
    </el-row>
    
      
</div>
</template>

<script>
    import box111 from '../Echarts/box111.vue';
    import box222 from '../Echarts/box222.vue';
    import box333 from '../Echarts/box333.vue';
    import box444 from '../Echarts/box444.vue';
    import box555 from '../Echarts/box555.vue';
    import box666 from '../Echarts/box666.vue';
    import ECharts from 'vue-echarts';

    export default{
      components:{box111,box222,box333,box444,box555,box666},
       data(){
         return {
        imgUrl1:require("../../assets/up.png"),
        imgUrl2:require("../../assets/mid.png"),
        imgUrl3:require("../../assets/down.png")
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
  .span {
    height: 250px;
  }
  .user-info {
    width: 100%;
      height: 250px;
  }
    .el-row {
    display: flex;
    /*margin-bottom: 10px;*/
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
    background: #0A5AAB;
  
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
    height: 250px;
  }
  .box2 {
    height: 250px;
    background-color: #053363;
  }
  .box3 {
    box-sizing: border-box;
    height: 250px;
  }
  .box4 {
    box-sizing: border-box;
    height: 250px;
  }
  .box5 {
    box-sizing: border-box;
    height: 250px;
  }
  .box6 {
    box-sizing: border-box;
    height: 250px;
  }
  .box7 {
    height: 250;
    box-sizing: border-box;
  }
</style>
<!-- <template>
    <div style="background-color: #053359;">
    <el-row :gutter="20">
      <el-col :span="16"><box1 class="grid-content bg-purple"></box1></el-col>
      <el-col :span="8"><box2 class="grid-content bg-purple1"></box2></el-col>
    </el-row>
    <el-row :gutter="20">
      <el-col :span="8"><box3 class="grid-content bg-purple"></box3></el-col>
      <el-col :span="8"><box4 class="grid-content bg-purple"></box4></el-col>
      <el-col :span="8"><box5 class="grid-content bg-purple1"></box5></el-col>
     
    </el-row>
    <el-row :gutter="20">
      <el-col :span="6"><box6 class="grid-content bg-purple1"></box6></el-col>
      <el-col :span="18"><box7 class="grid-content bg-purple"></box7></el-col>
      
    </el-row>
      
</div>
</template>

<script>
    import box1 from '../Echarts/box1.vue';
    import box2 from '../Echarts/box2.vue';
    import box3 from '../Echarts/box3.vue';
    import box4 from '../Echarts/box4.vue';
    import box5 from '../Echarts/box5.vue';
    import box6 from '../Echarts/box6.vue';
    import box7 from '../Echarts/box7.vue';
    import ECharts from 'vue-echarts'

    

    export default{
      components:{box1,box2,box3,box4,box5,box6,box7},
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
    background: #0A5AAB;

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
    height: 250px;
  }
  .box2 {
    height: 250px;
    background-color: #053363;
  }
  .box3 {
    box-sizing: border-box;
    height: 250px;
  }
  .box4 {
    box-sizing: border-box;
    height: 250px;
  }
  .box5 {
    box-sizing: border-box;
    height: 250px;
  }
  .box6 {
    box-sizing: border-box;
    height: 250px;
  }
  .box7 {
    height: 250;
    box-sizing: border-box;
  }
</style> -->