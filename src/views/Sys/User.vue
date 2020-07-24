<template>
    <div style="background-color: #fff;">
  <el-row :gutter="5">      
    <span class="span"><img class="user-info" :src="imgUrl1" /></span>

     <el-card class="box-cardnull">
      
      {{'经济正常'}}
      </el-card>

     
        <el-card class="box-card">
          <div slot="header" class="clearfix">
            <span>基本信息</span>
          </div>

          <el-row>
            <el-col><span >姓名:何宇翔</span></el-col>
            <el-col><span >性别:男</span></el-col>
          </el-row>
          <el-row>
            <el-col><span >身份证:440106XXXXXXXXX</span></el-col>
            <el-col><span >手机:1769XXXXXX</span></el-col>
          </el-row>
          <el-row>
            <el-col><span >电话:1769XXXXXX</span></el-col>
            <el-col><span >地址:广东省</span></el-col>
          </el-row>
          <el-row>
            <el-col><span >职业:学生</span></el-col>
            <el-col><span >备注:无</span></el-col>
          </el-row>
        </el-card>


      
     
    </el-row>


    <el-row :gutter="5">    
    <span class="span"><img class="user-info" :src="imgUrl2" /></span>  

    <el-card class="box-cardnull">
      <div>
        {{'社交活跃'}}
      </div>
      </el-card>

          <el-card class="box-card">
      <div slot="header" class="clearfix">
        <span>详细信息</span>
      </div>
      <el-row>
            <el-col><span >航行次数:12</span></el-col>
            <el-col><span >经济舱:10</span></el-col>
            <el-col><span >头等舱:2</span></el-col>
      </el-row>
      <el-row>            
            <el-col><span >本次交易金额:2000</span></el-col>
            <el-col><span >起点:Guangzhou</span></el-col>
            <el-col><span >终点:Tianjin</span></el-col>
      </el-row>
      <el-row>                  
      </el-row>
      <el-row> 
            <el-col><span >航空公司:南航</span></el-col>
            <el-col><span >医疗险次数:7</span></el-col>
            <el-col><span >意外险次数:8</span></el-col>
      </el-row>
      <el-row>          
            <el-col><span >手机交易次数:10</span></el-col>
            <el-col><span >页交易次数:2</span></el-col>
            <el-col><span >网页值机:12</span></el-col>
      </el-row>

    </el-card>
    </el-row>

    <el-row :gutter="5">   
    <span class="span"><img class="user-info" :src="imgUrl3" /></span>   


<el-card class="box-cardnull">
      
      {{'爱好广泛'}}
      </el-card>

       <el-card class="box-card">

      <el-row>
       <el-col ><china></china></el-col>
       <el-col  style="margin-bottom: 200px"><box333></box333></el-col>
     </el-row>


    </el-card>
     
    </el-row>
    
      
</div>
</template>

<script>

    import ECharts from 'vue-echarts';
    import china from '../Echarts/china.vue'
    import box333 from '../Echarts/box333.vue'

    export default{
      components:{china,box333},
       data(){
         return {
        imgUrl1:require("../../assets/up1.png"),
        imgUrl2:require("../../assets/mid1.png"),
        imgUrl3:require("../../assets/down1.png")
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
  /*.row-bg {
    padding: 10px 0;
    
  }*/
  .text {
    font-size: 14px;
  }

  /*.item {
    margin-bottom: 18px;
  }*/

  .clearfix:before,
  .clearfix:after {
    display: table;
    content: "";
  }
  .clearfix:after {
    clear: both
  }

  .box-card {
    width: 1000px;
    margin-left: 40px;
    height: 250px;
  }
  .box-cardnull {
    width: 200px;
    height: 60px;
    margin-top: 90px;
  }
</style>
<!-- <template>
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
</style> -->