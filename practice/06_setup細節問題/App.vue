<template>
  <h2>app</h2>
  <h3>msg:{{msg}}</h3>
  <button @click="msg +='==='" >update data</button>
  <hr/>
  <Child :msg="msg" @toolabClick="toolabFun" msg2='4545641'/>
</template>
<script lang="ts">
import { defineComponent ,ref} from 'vue'
//引入子級組件Child
import Child from './components/Child.vue'
export default defineComponent({
  name:'APP',

  //註冊組件
  components:{
    Child
  },

  setup(){
   
    const msg=ref('what are you')
    function toolabFun(key:string){
      console.log('aaa'+key)
      msg.value+=key
    }
    return{
      msg,
      toolabFun
    }
  }
})
</script>