<template>
  <div class="home">
    <PageHead :list="listData"></PageHead>
    <div class="img-container">
      <ImgSlide :imgData="imgData"></ImgSlide>
    </div>
  </div>
</template>

<script>
import PageHead from '@/components/common/page-regions/Header';
import ImgSlide from '@/components/common/plugins/ImgSlide';

export default {
  name: 'home'
  ,data () {
    return {
      listData: [
        {
          name:"建材1"
          ,type:"home"
          ,id:"111"
          ,isActive:true
          ,children:[{
            name:"一级建材"
            ,type:"home1"
          }]
        },{
          name:"建材2"
          ,type:"test"
          ,id:"222"
          ,isActive:false
          ,children:[{
            name:"二级建材"
            ,type:"test1"
          }]
        }
      ]
      ,imgData:{
        list:[
          {
            src:"1.jpg"
            ,id:"1"
          }
          ,{
            src:"2.jpg"
            ,id:"2"
          }
          ,{
            src:"3.jpg"
            ,id:"3"
          }
        ]
        ,showSmallImg:false
        ,showSircle:true
      }
    }
  }
  ,components:{
    PageHead
    ,ImgSlide
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .img-container{
    width: 1150px;
    margin: 10px auto;
  }

</style>
