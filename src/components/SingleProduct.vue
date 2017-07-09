<template>
  <div class="male-single">
    <RegionTitle :titData="titData"></RegionTitle>
    <ul class="img-con">
      <li v-for="(item,index) in maleSingleData" :key="item.index" v-bind:class="item.type">
        <a href="javascript:;" :id="index" >
            <img v-bind:src="item.imgSrc" >
            <div class="price-con" v-if="{true : item.type == sell}" >
                <div class="name">{{item.name}}</div>
                <div class="price">
                    <span class="sell-price">{{item.price}}</span>
                    <span class="origin-price">{{item.originPrice}}</span>
                </div>
            </div>
        </a>
      </li>
    </ul>
  </div>
</template>
<script>
import RegionTitle from './base/regionTitle';

export default {
  name:"SingleProduct"
  ,props:["maleSingleData"]
  ,data:function(){
      return {
        "titData":{
            title:"人气单品"
            ,src:"###"
        }
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
    }
    .male-single .img-con a{
        width: 100%;
        height: 100%;
        display: block;
        position: relative;
        background: #F5F7F6;
    }
    .male-single .img-con li{
        float:left;
        margin-left: 6px;
        margin-bottom: 8px;
    }
    .male-single .img-con li.sell img{
        width: 185px;
        height: 248px;
    }
    .male-single .img-con li:hover{
        opacity: 0.8;
    }
    .male-single .img-con li.activity img{
        width: 378px;
        height: 248px;
    }
    .male-single .img-con li.banner img{
        width: 100%;
        height: 129px;
    }
    .price-con{
        position: absolute;
        bottom: 5px;
        width: 100%;
        text-align: center;
        color: #000;
    }
    .price,
    .name{
        padding-bottom: 5px;
    }
    .sell-price{
        padding-right: 10px;
    }
    .origin-price{
        text-decoration: line-through
    }
</style>
