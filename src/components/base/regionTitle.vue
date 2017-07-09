<template>
  <div class="region-tit">
    <h1>{{titData.title}}</h1>
    <a v-if="titData.src" href="titData.src">MORE</a>
  </div>
</template>
<script>
export default {
  name:"RegionTitle"
  ,props:["titData"]
}
</script>
<style scope>
    .region-tit{
      position: relative;
    }
    .region-tit a{
      position: absolute;
      right: 0;
      top: 10px;
      color: #333;
      text-decoration: none;
    }
    .region-tit h1{
      width: 288px;
      height: 31px;
      margin: 0 auto;
      line-height: 31px;
      border: 1px solid #000;
      font-size: 16px;
      text-align: center;
    }
</style>
