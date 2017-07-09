<template>
  <div class="img-slide">
    <span class="iconfont icon-up" v-on:click="goPrev"></span>
    <span class="iconfont icon-down" v-on:click="goNext"></span>
    <ul class="big-img-con">
      <li v-for="(item,index) in imgData.list" :key="item.index">
        <a href="javascript:;" :id="index" >
          <transition name="fade">
            <img v-bind:src="item.src" v-bind:class="{active : index == activeIndex}" v-show="{true : index == activeIndex}">
          </transition>
        </a>
      </li>
    </ul>
    <div class="sircle-con" v-if="imgData.showSircle" >
      <span v-for="(item,index) in imgData.list" :key="item.index" >
        <a href="javascript:;" 
          :id="index" 
          v-on:mouseenter="changeActive"
          v-bind:class="[item.index == activeIndex ? active : '','iconfont']" 
        ></a>
      </span>
    </div>
    <ul class="small-con" v-if="imgData.showSmallImg">
      <li v-for="(item,index) in imgData.list" :key="item.index">
        <a href="javascript:;">
          <img  :id="index" v-on:mouseenter="changeActive"
            v-bind:src="item.src" 
            v-bind:class="{active : index == activeIndex}"
          >
        </a>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  name:"ImgSlide"
  ,props:["imgData"]
  ,data:function(){
    let activeIndex = 0;
    return {activeIndex:activeIndex}
  }
  ,methods:{
    changeActive:function(e){
      let ele = e.target;
      this.activeIndex = ele.id;
      return this.activeIndex;
    }
    ,goPrev:function(){
      this.activeIndex--;
      if(this.activeIndex < 0)
        this.activeIndex = this.imgData.list.length-1;
    }
    ,goNext:function(){
      this.activeIndex++;
      if(this.activeIndex > this.imgData.list.length-1)
        this.activeIndex = 0;
    }
  }
  ,created (){
    this.imgInterval = setInterval(() => {
      this.activeIndex++;
      if(this.activeIndex > this.imgData.list.length-1)
        this.activeIndex = 0;
    }, 5*1000)
  }
}
</script>
<style scope>
  ul,li{
    list-style-type: none;
  }
  .img-slide{
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
    width: 60px;
    height: 60px;
    top: 50%;
    margin-top:-30px;
    background: rgba(255,255,255,0.2);
    cursor: pointer;
    z-index: 1;
  }
  span.iconfont:before{
    font-size: 3em;
  }
  .icon-up{
    left: 0;
    cursor: pointer;
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
  .img-slide .big-img-con img{
    display: none;
  }
  .img-slide .big-img-con img.active{
    display: inline;
  }
  .img-slide ul.big-img-con{
    position: relative;
  }
  .img-slide ul.big-img-con,
  .img-slide ul.big-img-con li,
  .img-slide img{
    width: 100%;
    height: 450px;
  }
  .img-slide ul.big-img-con li,
  .img-slide ul.big-img-con img{
    position: absolute;
    left: 0;
    top: 0;
  }
  /*sircle-con*/
  .sircle-con{
    position: absolute;
    text-align: center;
    bottom: 74px;
    width: 100%;
  }
  .sircle-con a.iconfont{
    background: rgba(0,0,0,0.2);
    cursor: pointer;
    font-size: 2em;
    text-decoration: none;
  }
  .sircle-con a.iconfont:before{
    content: "\e7e0";
    color: rgba(255,255,255,0.6);
  }
  .sircle-con a.iconfont:hover::before,
  .sircle-con a.iconfont.active::before{
    color: rgba(255,255,255,1);
  }
  .sircle-con span:first-child a.iconfont{
    border-top-left-radius: 50%;
    border-bottom-left-radius: 50%;
  }
  .sircle-con span:last-child a.iconfont{
    border-top-right-radius: 50%;
    border-bottom-right-radius: 50%;
  }
  /*small-con*/
  .small-con{
    margin-top: 6px;
    height: 54px;
  }
  .small-con ul{
    overflow: hidden;
  }
  .small-con li{
    float: left;
    margin-left: 6px;
    width: 138px;
    height: 54px;
    cursor: pointer;
    opacity: 0.7;
  }
  .small-con li a{
    display: block;
    width: 100%;
    height: 100%;
  }
  .small-con li:hover{
    opacity: 1;
  }
  .small-con li:first-child{
    margin-left: 2px;
  }
  .small-con li,
  .small-con li img{
    width: 138px;
    height: 54px;
  }
  /*ranstion*/
  .fade-enter-active, .fade-leave-active {
    transition: opacity .5s
  }
  .fade-enter, .fade-leave-to /* .fade-leave-active in <2.1.8 */ {
    opacity: 0
  }
</style>

