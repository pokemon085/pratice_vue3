<template>
<div>setup和ref的基本使用</div>
<h3>{{count}}</h3>
<button @click="updateCount">update data</button>
</template>

<script lang="ts">
import {defineComponent,ref} from 'vue';
export default defineComponent({
  name:'App',
  //需求:打開頁面後可以直接看到一個數據 點擊按鈕後 該數據可以產生變化
  //vue2實現
  // data(){
  //   return{
  //     count:0
  //   }
  // },
  // methods:{
  //   updateCount(){
  //     this.count++;
  //   }
  // }

  //vue3實現
  setup(){
    //變量
    //ref是一個函數 定義一個響應式的數據
    //一般用來定義一個基本類型的響應式數據
    let count=ref(0);
    console.log(count);//印出來會返回一個Ref對象 需要從裡面給的value屬性來取值 才能操作數據
    //html模板中不需要加上.value屬性

    //方法
    function updateCount(){
      count.value++ //操作數據
      //count++ ref是對象 不能++ 一定要在後面加.value
    }

    //返回的是一個對象
    return {
      //屬性
      count,

      //方法
      updateCount

    }
  }
})
</script>

<style lang="scss">

</style>
