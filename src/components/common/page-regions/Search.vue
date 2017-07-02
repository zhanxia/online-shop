<template>
  <div class="searcher">
    <div class="form-input">
        <input type="text" placeholder="建材" class="search-input">
        <span class="search-icon"></span>
        <span class="shop-cart"></span>
    </div>
    <div class="search-links">
        <a v-for="(item,index) in searchLinks" :key="item.index" >
            <span :title="item.name">{{item.name}}</span>
        </a>
    </div>
  </div>
</template>
<script>
export default {
  name:"Searcher"
  ,data () {
    return {
      searchLinks:[{
          name:"建材"
          ,id:"111"
      },{
          name:"建材"
          ,id:"111"
      },{
          name:"建材"
          ,id:"111"
      },{
          name:"建材"
          ,id:"111"
      }]
    }
  }
}
</script>
<style scoped>
  .searcher{
      float: right;
  }
  .form-input{
      overflow: hidden;
  }
  .search-input{
    float: left;
    border: 1px solid #3a3a3a;
    padding-left: 10px;
    width: 229px;
    height: 26px;
  }
  .search-icon{
      display: block;
      float: left;
      width: 78px;
      height: 28px;
      background: url('../../../../static/images/search.png') center no-repeat;
      background-color: #3a3a3a;
      cursor: pointer;
  }
  .shop-cart{
      display: block;
      float: left;
      background: url('../../../../static/images/icons.png') no-repeat;
      background-position: -228px 0;
      width: 30px;
      height: 30px;
      background-size: contain;
  }
  .search-links{
      width: 320px;
      overflow: hidden;
      margin-top: 6px;
  }
  .search-links a{
    color: #b0b0b0;
    vertical-align: baseline;
    padding-right: 18px;
    height: 16px;
    cursor: pointer;
  }
  .search-links a:hover,
  .search-links a:active{
      color: #d0021b;
  }
</style>

