<template>
  <div class="img-slide">
    <span class="iconfont icon-up"></span>
    <span class="iconfont icon-down"></span>
    <ul>
      <li v-for="(item,index) in imgData.list" :key="item.index">
        <a href="javascript:;" :id="item.index" v-on:click="changeActive">
          <img src="item.src" v-bind:class="{active : item.index == activeIndex}">
        </a>
      </li>
    </ul>
    <div  class="sircle-con" v-if="showSircle"></div>
  </div>
</template>
<script>
export default {
  name:"ImgSlide"
  ,props:["imgData"]
  ,computed: {
    activeIndex: function () {
      return "0";
    }
  }
  ,methods:{
    changeActive:function(e){
      let ele = e.target;
      this.imgData.list.forEach((item) => {
        activeIndex = item.id;
      });
    }
  }
}
</script>
<style scope>
  ul,li{
    list-style-type: none;
  }
  .img-slide{
    height: 450px;
    position: relative;
    background: rebeccapurple;
  }
  @font-face {
    font-family: "iconfont";
    src: url('../../../../static/fonts/iconfont.eot?t=1499091831944'); /* IE9*/
    src: url('../../../../static/fonts/iconfont.eot?t=1499091831944#iefix') format('embedded-opentype'), /* IE6-IE8 */
    url('../../../../static/fonts/iconfont.woff?t=1499091831944') format('woff'), /* chrome, firefox */
    url('../../../../static/fonts/iconfont.ttf?t=1499091831944') format('truetype'), /* chrome, firefox, opera, Safari, Android, iOS 4.2+*/
    url('../../../../static/fonts/iconfont.svg?t=1499091831944#iconfont') format('svg'); /* iOS 4.1- */
  }
  .iconfont {
    font-family:"iconfont" !important;
    font-size:16px;
    font-style:normal;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }
  span.iconfont{
    display: block;
    position: absolute;
    width: 60px;
    height: 60px;
    top: 50%;
    margin-top:-30px;
    background: blueviolet;
    cursor: pointer;
  }
  span.iconfont:before{
    font-size: 3em;
  }
  .icon-up{
    left: 0;
  }
  .icon-up:before{
    content: "\e600";
    position: absolute;
    left: 10px;
    top: 5px;
  }
  .icon-down{
    right: 0;
  }
  .icon-down:before{
    content: "\e601";
    position: absolute;
    right: 10px;
    top: 5px;
  }
  /*imgs*/
  .img-slide img{
    display: none;
  }
  .img-slide img.active{
    display: inline;
  }
  .img-slide ul,
  .img-slide li,
  .img-slide img{
    width: 100%;
    height: 100%;
  }
  /*sircle-con*/
  .sircle-con{
    position: absolute;
    background: rgba(0, 0, 0, 0.3);
    
  }
</style>

