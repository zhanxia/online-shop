<template>
  <ul class="links-con">
    <li v-for="(item,index) in linkData" :key="item.index" v-bind:class="item.type">
        <a href="item.src" :id="index" >
            {{item.name}}
        </a>
    </li>
  </ul>
</template>
<script>
/*折扣区图片*/
export default {
  name:"GoodsLink"
  ,props:["linkData"]
}
</script>
<style scope>
    .links-con{
        height: 228px;
        padding: 10px 0;
        background-color: #f8f8f8;
        overflow: hidden;
    }
    .links-con a{
        float: left;
        width: 50%;
        text-align: center;
        color: #000;
        overflow: hidden;
        text-decoration: none;
        height: 38px;
        line-height: 38px;
        font-size: 14px;
    }
</style>
