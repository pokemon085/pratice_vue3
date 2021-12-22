<template>
  <div>
    <h2>子級組件</h2>
    <div>{{ msg }}</div>
    <button @click="update">更新</button>
  </div>
</template>
<script lang="ts">
import { defineComponent,ref,  onMounted,
  onUpdated,
  onUnmounted,
  onBeforeMount,
  onBeforeUpdate,
  onBeforeUnmount } from 'vue'
export default defineComponent({
   name:'Child',
  
    setup(){

      console.log('setup')
      const msg = ref('abc')

    const update = () => {
      msg.value += '--'
    }
    onBeforeMount(() => {
      console.log('--onBeforeMount')
    })

    onMounted(() => {
      console.log('--onMounted')
    })

    onBeforeUpdate(() => {
      console.log('--onBeforeUpdate')
    })

    onUpdated(() => {
      console.log('--onUpdated')
    })

    onBeforeUnmount(() => {
      console.log('--onBeforeUnmount')
    })

    onUnmounted(() => {
      console.log('--onUnmounted')
    })
    
    return{
      msg,update
    }
    }

})

</script>
