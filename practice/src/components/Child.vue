<template>
<h2>child</h2>
<h3>msg:{{msg}}</h3>
</template>
<script lang="ts">
import { defineComponent } from 'vue'
export default defineComponent({
    name:'Child',
    props:['msg'],
    

    //數據初始化的生命週期回調
    beforeCreate(){
        console.log('beforecreate')
    },

    //setup會在beforeCreate前就執行了
    //setup在執行的時候 當前組件還沒有創建出來 this不能用會undefined
    setup(){
        console.log('setup')
        return{

        }
    }
})
</script>