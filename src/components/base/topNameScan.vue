<template>
  <ul class="topnscan-con">
    <li v-for="(item,index) in topNameData" :key="item.index" v-bind:class="item.type">
        <a href="javascript:;" :id="index" >
            <img v-bind:src="item.imgSrc" >
        </a>
        <div v-if="item.name" class="tops-name">
            <div class="name">{{item.name}}</div>
            <div class="des">{{item.des}}</div>
        </div>
    </li>
  </ul>
</template>
<script>
export default {
  name:"TopNameScan"
  ,props:["topNameData"]
}
</script>
<style scope>
    .topnscan-con{
        overflow: hidden;
    }
    .topnscan-con li{
        margin-right: 10px;
        margin-bottom: 8px;
        float: left;
        position: relative;
    }
    .topnscan-con li:last-child{
        margin-right: 0;
    }
    .topnscan-con li:hover{
        opacity: 0.8;
    }
    .topnscan-con li img{
        width: 222px;
        height: 298px;
    }
    .topnscan-con li a{
        display: block;
        width: 100%;
        height: 100%;
    }
    .topnscan-con .tops-name{
        position: absolute;
        bottom: 0;
        width: 100%;
        text-align: center;
        color: #2C2C2C;
        font-size: 14px;
        padding-bottom: 15px;
    }
    .topnscan-con .tops-name .des{
        color:#777777;
        margin-top: 8px;
    }
</style>
