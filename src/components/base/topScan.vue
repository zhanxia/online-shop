<template>
  <ul class="topscan-con">
    <li v-for="(item,index) in topScanData" :key="item.index" v-bind:class="item.type">
        <a href="javascript:;" :id="index" >
            <img v-bind:src="item.imgSrc" >
        </a>
        <div v-if="item.name" class="top-name">
            {{item.name}}
        </div>
    </li>
  </ul>
</template>
<script>
export default {
  name:"TopScan"
  ,props:["topScanData"]
}
</script>
<style scope>
    .topscan-con{
        overflow: hidden;
    }
    .topscan-con li{
        margin-left: 8px;
        margin-bottom: 8px;
        float: left;
        position: relative;
    }
    .topscan-con li:hover{
        opacity: 0.8;
    }
    .topscan-con li.big,
    .topscan-con li.big img{
        width: 378px;
        height: 248px;
    }
    .topscan-con li.small,
    .topscan-con li.small img{
        width: 185px;
        height: 248px;
    }
    .topscan-con li a{
        display: block;
        width: 100%;
        height: 100%;
    }
    .top-name{
        position: absolute;
        bottom: 0;
        width: 100%;
        text-align: center;
        line-height: 50px;
        color: #2C2C2C;
        background-color: #F5F7F6;
    }
</style>
