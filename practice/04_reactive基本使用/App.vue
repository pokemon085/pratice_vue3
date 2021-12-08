<template>
<div>reactive使用</div>
<h3>name:{{user.name}}</h3>
<h3>age:{{user.age}}</h3>
<h3>wife:{{user.wife}}</h3>
<h3>gender:{{user.gender}}</h3>
<button @click="updateUser">updateData</button>
</template>

<script lang="ts">
import {defineComponent, reactive} from 'vue';
export default defineComponent({
  name:'App',
  //需求:顯示用戶的相關訊息 點擊按鈕 可以更新用戶的相關訊息數據
  /*
  reactive 定義多個數據的響應式
  const proxy=reactive(obj) 接收一個普通對象然後返回普通對象的響應式代理器對象
  響應式轉換式深層的 會影響對象內部所有嵌套的屬性
  內部基於 ES6的 Proxy實現 通過代理對象操作源對象內部數據都是響應式的
   */
  setup(){
    //把數據變成響應式的數據
    //返回的是一個Proxy的代理對象,被代理者的目標對象就是obj對象
    //user現在是代理對象 obj是目標對象

    //加any 為了加上新的obj 屬性 obj.gender='boy' 要不然會報錯
   // const obj:any={
    const obj={  
      name:'aa',
      age:20,
      wife:{
        name:'bbb',
        age:18,
        cars:['mmm','nnn','ooo']
      }
    }
    const user=reactive<any>(obj)

    // const user=reactive<any>({
    //   name:'aa',
    //   age:20,
    //   wife:{
    //     name:'bbb',
    //     age:18,
    //     cars:['mmm','nnn','ooo']
    //   }
    // })

    console.log(user)

    //方法
    const updateUser=()=>{
      //修改資料
      user.name+="red"
      user.wife.name+="ccc"
      user.wife.cars[0]+='pppp'

      //新增obj gender屬性
      user.gender='boy'

      //刪除obj裡面age屬性
      delete user.age
    }
    return{
      user,
      updateUser
    }
  }

})
</script>

<style lang="scss">

</style>
