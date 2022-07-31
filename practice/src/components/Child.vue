<template>
<h2>child</h2>
<h3>msg:{{msg}}</h3>
<button @click="emitXxx">分發事件</button>
<br>
<slot name="aaa"></slot>
</template>
<script lang="ts">
import { defineComponent } from 'vue'
export default defineComponent({
    name:'Child',
    props:['msg','msg2'],
    emits:['toolabClick'],  //要emits出去 還要在子組件先聲明
    

    //數據初始化的生命週期回調
    beforeCreate(){
        console.log('beforecreate')
    },

    //setup會在beforeCreate前就執行了
    //setup在執行的時候 當前組件還沒有創建出來 this不能用會undefined

    setup(props,{attrs,slots,emit}){
    //setup(props,context){
        
        /*context參數 是一個對象 裡面有
         attrs對象(獲取當前組件標籤上的所有屬性的對象 但是該屬性是在props中沒有聲明接收的對象)
         emit方法 
         slots對象
        */
       // console.log(context.attrs.msg2)
       // console.log(context)
        //console.log(attrs.msg2)


        //按鈕的點擊事件的回調函數
        function emitXxx(){
            console.log('aaa')
          //  context.emit('toolabClick','+=+');  
          emit('toolabClick','+=+')
        }
        

        console.log('setup')
        return{
            emitXxx
        }
    }
})
</script>