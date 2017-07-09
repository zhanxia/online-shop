<template>
  <div class="male-single">
    <RegionTitle :titData="titData"></RegionTitle>
    <div class="img-con">
        <ul class="img-start-con">
        <li v-for="(item,index) in newSelectStartData" :key="item.index" v-bind:class="item.type">
            <a href="javascript:;" :id="index" >
                <img v-bind:src="item.imgSrc" >
            </a>
        </li>
        </ul>
        <ul class="img-end-con">
            <li v-for="(item,index) in newSelectEndData" :key="item.index" v-bind:class="item.type">
                <a href="javascript:;" :id="index" >
                    <img v-bind:src="item.imgSrc" >
                </a>
            </li>
        </ul>
    </div>
  </div>
</template>
<script>
import RegionTitle from './base/regionTitle';

export default {
  name:"NewSletter"
  ,props:["newSletterData"]
  ,data:function(){
      return {
        "titData":{
            title:"人气单品"
            ,src:"###"
        }
        ,"newSelectStartData":this.newSletterData.slice(0,this.newSletterData.length-1)
        ,"newSelectEndData":this.newSletterData.slice(this.newSletterData.length-1)
      }
  }
  ,components:{
    RegionTitle
  }
}
</script>
<style scope>
    .male-single .img-con{
        margin-top: 40px;
        overflow: hidden;
    }
    .male-single .img-start-con{
        width: 868px;
        float: left;
    }
    .male-single .img-end-con{
        float: right;
    }
    .male-single .img-con a{
        width: 100%;
        height: 100%;
        display: block;
    }
    .male-single .img-start-con li{
        float:left;
        margin-left: 6px;
        margin-bottom: 8px;
    }
    .male-single .img-end-con li{
        margin-left: 0;
    }
    .male-single .img-con li:hover{
        opacity: 0.8;
    }
    .male-single .img-con li.big img,
    .img-end-con li.big img{
        width: 282px;
        height: 504px;
    }
    .male-single .img-con li.small img{
        width: 185px;
        height: 248px;
    }
</style>
