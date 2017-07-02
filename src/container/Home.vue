<template>
  <div class="home">
    <PageHead :list="listData"></PageHead>
  </div>
</template>

<script>
import PageHead from '@/components/common/page-regions/Header';

export default {
  name: 'home'
  ,data () {
    return {
      listData: [{
        name:"建材1"
        ,type:"home"
        ,id:"111"
        ,isActive:true
        ,children:[{
          name:"一级建材"
          ,type:"home1"
        }]
      },{
        name:"建材2"
        ,type:"test"
        ,id:"222"
        ,isActive:false
        ,children:[{
          name:"二级建材"
          ,type:"test1"
        }]
      }]
    }
  }
  ,components:{PageHead}

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>


</style>
