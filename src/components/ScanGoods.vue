<template>
  <div class="male-single">
    <RegionTitle :titData="titData"></RegionTitle>
    <div class="scan-con">
        <div class="links-area">
            <Discount :discountData="scanData.discountData"></Discount>
            <GoodsLink :linkData="scanData.linkData"></GoodsLink>
        </div>
        <TopScan :topScanData="scanData.topData"></TopScan>
        <TopNameScan :topNameData="scanData.topNameData"></TopNameScan>
    </div>
  </div>
</template>
<script>
import RegionTitle from './base/regionTitle';
import Discount from './base/Discount';
import TopScan from './base/topScan';
import TopNameScan from './base/topNameScan';
import GoodsLink from './base/GoodsLink';

export default {
  name:"ScanGoods"
  ,props:["scanData"]
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
    ,Discount
    ,TopScan
    ,GoodsLink
    ,TopNameScan
  }
}
</script>
<style scope>
    .male-single,
    .scan-con{
        margin-top: 40px;
    }
    .links-area{
        float: left;
    }
</style>
