<template>
  <div class="img-page">
    <div class="img-con">
        <ul class="brand-img-con">
            <li v-for="(item,index) in countImgData" :key="item.index">
                <a href="javascript:;" :id="index" >
                    <img v-bind:src="item.src" >
                </a>
            </li>
        </ul>
    </div>
    <div class="control-con">
        <div class="icons">
            <span class="iconfont icon-up" v-on:click="goPrev"></span>
            <span class="iconfont icon-down" v-on:click="goNext"></span>
        </div>
        <div class="more">
            <a href="###">MORE  ></a>
        </div>
    </div>
  </div>
</template>
<script>
export default {
  name:"ImgPage"
  ,props:["imgData"]
  ,data:function(){
    let activeIndex = 0;
    return {
        activeIndex:activeIndex
    }
  }
  ,computed: {
    countImgData: function () {
        let countImgData;
        let length = this.activeIndex*10+10;
        return this.imgData.slice(this.activeIndex*10,length);
    }
  }
  ,methods:{
    goPrev:function(){
      this.activeIndex--;
      if(this.activeIndex < 0){
        this.activeIndex = (this.imgData.length/10)-1;
      }
    }
    ,goNext:function(){
      this.activeIndex++;
      if(this.activeIndex > (this.imgData.length/10)-1){
        this.activeIndex = 0;
      }
    }
  }
}
</script>
<style scope>
  ul,li{
    list-style-type: none;
  }
  .img-page{
    position: relative;
  }
  @font-face {
    font-family: "iconfont";
    src: url('../../../static/fonts/iconfont.eot?t=1499091831944'); /* IE9*/
    src: url('../../../static/fonts/iconfont.eot?t=1499091831944#iefix') format('embedded-opentype'), /* IE6-IE8 */
    url('../../../static/fonts/iconfont.woff?t=1499091831944') format('woff'), /* chrome, firefox */
    url('../../../static/fonts/iconfont.ttf?t=1499091831944') format('truetype'), /* chrome, firefox, opera, Safari, Android, iOS 4.2+*/
    url('../../../static/fonts/iconfont.svg?t=1499091831944#iconfont') format('svg'); /* iOS 4.1- */
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
    width: 40px;
    height: 40px;
    top: 50%;
    margin-top:-20px;
    background: rgba(255,255,255,0.2);
    cursor: pointer;
    z-index: 1;
  }
  .img-page .icons span.iconfont:before{
    font-size: 1.6em;
    font-weight: bold;
  }
  .img-page .icons .icon-up{
    left: 0;
    cursor: pointer;
  }
  .img-page .icons .icon-up:before{
    content: "\e600";
    position: absolute;
    left: 60px;
    top: 0;
  }
  .img-page .icons .icon-down{
    right: 0;
  }
  .img-page .icons .icon-down:before{
    content: "\e601";
    position: absolute;
    right: 70px;
    top: 20px;
  }
  /*imgs*/
  .img-page .img-con{
      float: left;
      width: 965px;
  }
  .img-page .control-con{
      overflow: hidden;
  }
  .img-page ul.brand-img-con li{
    float: left;
    margin: 8px 8px 0 0;
  }
  .img-page ul.brand-img-con li,
  .img-page ul.brand-img-con li a,
  .img-page ul.brand-img-con li img{
    width: 185px;
    height: 86px;
    line-height: 86px;
    font-size: 0;
    text-align: center;
  }
  .img-page ul.brand-img-con li:hover{
      opacity: 0.8;
  }
  /*control*/
  .img-page .icons,
  .img-page .more{
    width: 185px;
    height: 86px;
    margin-top: 8px;
  }
  .img-page .icons{
      position: relative;
      background: url(../../../static/images/logo-brand-line.png) center no-repeat;
  }
  .img-page .more{
      line-height: 86px;
      text-align: center;
  }
  .img-page .more a{
      text-decoration: none;
      color: #000;
  }
</style>

