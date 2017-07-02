<template>
  <div class="header">
    <div class="header-nav">
      <ul class="nav">
        <li v-for="(item, index) in list" 
            :key="item.index" 
        >
          <a v-bind:class="{active: item.isActive}"
            v-bind:id="item.id"
            v-on:click="changeActive"
          >
            {{item.name}}
          </a>
        </li>
      </ul>
      <Logo></Logo>
      <Searcher></Searcher>
    </div>
    <div class="sub-nav">
      <ul class="sub-nav-list" v-for="(item,index) in subNavList" :key="item.index">
        <a>{{item.name}}</a>
      </ul>
    </div>
  </div>
</template>
<script>
import Searcher from '@/components/common/page-regions/Search';
import Logo from '@/components/common/page-regions/Logo';

export default {
  name:"PageHead"
  ,props:["list"]
  ,data () {
    return {
      items:""
    }
  }
  ,components:{Searcher,Logo}
  ,computed: {
    subNavList: function () {
      let subNavList;
      this.list.forEach((item) => {
        if(item.isActive)
          subNavList = item.children;
      });
      return subNavList;
    }
  }
  ,methods:{
    changeActive:function(e){
      let ele = e.target;
      this.list.forEach((item) => {
        item.isActive = item.id == ele.id ? true : false;
      });
    }
  }
}
</script>
<style scoped>
  *{
    font-size: 14px;
    color: #000;
    font-family: "arial, SimHei";
    margin: 0;
    padding: 0;
  }
  ul,li{
    list-style-type: none;
    margin: 0;
    padding: 0;
  }
  .header-nav{
    width: 1150px;
    margin: 40px auto 0;
    position: relative;
  }
  .nav{
    float: left;
  }
  .nav li{
    float: left;
  }
  .nav li a{
    display: inline-block;
    padding: 19px 22px;
    font-size: 16px;
    background-color: #fff;
    cursor: pointer;
  }
  .nav li a.active{
    background-color: #3a3a3a;
    color: #fff;
  }
  .sub-nav{
    width: 100%;
    clear: both;
    background-color: #3a3a3a;
    height: 40px;
    line-height: 40px;
  }
  .sub-nav-list{
    width: 1150px;
    margin: 0 auto;
  }
  .sub-nav-list a{
    color: #fff;
    text-decoration: underline;
    padding-right: 82px;
    cursor: pointer;
  }
</style>

