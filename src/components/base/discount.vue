<template>
  <ul class="discount-con">
    <li v-for="(item,index) in discountData" :key="item.index" v-bind:class="item.type">
        <a href="javascript:;" :id="index" >
            <img v-bind:src="item.imgSrc" >
        </a>
    </li>
  </ul>
</template>
<script>
/*折扣区图片*/
export default {
  name:"Discount"
  ,props:["discountData"]
}
</script>
<style scope>
    .discount-con li{
        margin-bottom: 10px;
    }
    .discount-con li.big,
    .discount-con li.big img{
        width: 185px;
        height: 152px;
    }
    .discount-con li.small,
    .discount-con li.small img{
        width: 185px;
        height: 86px;
    }
    .discount-con li a{
        display: block;
        width: 100%;
        height: 100%;
    }
</style>
