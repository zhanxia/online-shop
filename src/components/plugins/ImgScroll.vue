<template>
  <div class="img-scroll">
    <span class="iconfont icon-up" v-on:click="goPrev"></span>
    <span class="iconfont icon-down" v-on:click="goNext"></span>
    <div class="show-region" ref="showContainer" 
        v-on:mouseenter="clearInterval" 
        v-on:mouseleave="startInterval"
    >
        <ul class="big-img-con">
            <li v-for="(item,index) in imgData" :key="item.index">
                <a href="javascript:;" :id="index" >
                    <img v-bind:src="item.src" >
                </a>
            </li>
        </ul>
    </div>
  </div>
</template>
<script>
export default {
  name:"ImgScroll"
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
      if(this.activeIndex < 0){
        this.activeIndex = (this.imgData.length/3)-1;
      }
      this.countScrollLeft();
    }
    ,goNext:function(){
      this.activeIndex++;
      if(this.activeIndex > (this.imgData.length/3)-1){
        this.activeIndex = 0;
      }
      this.countScrollLeft();
    }
    ,countScrollLeft (){
        let self = this;
        // let left = parseInt(self.activeIndex) * self.$refs.showContainer.clientWidth;
        // let scrollt = setInterval(function(){
        //     let now = self.$refs.showContainer.scrollLeft;
        //     if(now < left){
        //         now += 50;
        //         self.$refs.showContainer.scrollLeft = now;
        //     }
        // },17)
        self.$refs.showContainer.scrollLeft = parseInt(self.activeIndex) * self.$refs.showContainer.clientWidth;
    }
    ,startInterval(){
        let self = this;
        this.imgInterval = setInterval(() => {
            self.activeIndex++;
            if(self.activeIndex > (self.imgData.length/3)-1){
                self.activeIndex = 0;
            }
            self.countScrollLeft();
        }, 5*1000)
    }
    ,clearInterval(){
        clearInterval(this.imgInterval);
        this.imgInterval = null;
    }
  }
  ,mounted (){
    this.startInterval();
  }
}
</script>
<style scope>
  ul,li{
    list-style-type: none;
  }
  .img-scroll{
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
  span.iconfont:before{
    font-size: 1.6em;
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
  .img-scroll .big-img-con img.active{
    display: inline;
  }
  .img-scroll ul.big-img-con{
    width: 10000px;
    overflow: scroll;
    /*overflow-y: hidden;*/
  }
  .img-scroll ul.big-img-con li,
  .img-scroll img{
    width: 378px !important;
    height: 175px;
  }
  .img-scroll ul.big-img-con li{
    float: left;
    margin-right: 8px;
  }
  .img-scroll ul.big-img-con li:hover{
      opacity: 0.8;
  }
  .img-scroll ul.big-img-con li:nth-child(3n){
    margin-right: 0;
  }
  /*show-region*/
  .show-region{
      width: 100%;
      overflow: hidden;
      height: 175px;
  }
</style>

