<template>
    <div>
    <h2>app 父級組件</h2>
    <button @click="isShow=!isShow">切換</button>
    <hr/>
    <Child v-if="isShow"/>
    </div>
</template>
<script lang="ts">
import Child from './components/Child.vue'
import { defineComponent,ref } from 'vue'
export default defineComponent({
    name:'APP',
    components:{
        Child
    },
    setup(){
      const isShow=ref(true)
      return{
        isShow
      }
    }
})
</script>