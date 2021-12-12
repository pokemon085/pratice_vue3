<template>
  <div>
    <h2>計算屬性與監聽</h2>
    <fieldset>
      <legend>姓名操作</legend>
      姓氏:
      <input
        type="text"
        placeholder="請輸入姓氏"
        v-model="user.firstName"
      /><br />
      名字:
      <input
        type="text"
        placeholder="請輸入名字"
        v-model="user.lastName"
      /><br />
    </fieldset>
    <fieldset>
      <legend>計算屬性和監視</legend>
      姓名:
      <input type="text" placeholder="顯示姓名" v-model="fullName1" /><br />
      姓名:
      <input type="text" placeholder="顯示姓名" v-model="fullName2" /><br />
      姓名: <input type="text" placeholder="顯示姓名"  v-model="fullName3"  /><br />
    </fieldset>
  </div>
</template>
<script lang="ts">
import { defineComponent, reactive, computed ,watch,ref,watchEffect} from "vue";
export default defineComponent({
  name: "APP",

  setup() {
    const user = reactive({
      firstName: "aaa",
      lastName: "bbb",
    });

    const fullName1 = computed(() => {
      return user.firstName + "_" + user.lastName;
    });

    //下面更改字 上面也會更著改
    const fullName2 = computed({
      get() {
        return user.firstName + "_" + user.lastName;
      },
      set(val: string) {
        console.log("===" + val);
        const names = val.split("_");
        if (names) {
          user.firstName = names[0];
          user.lastName = names[1];
        }
      },
    });

    const fullName3=ref('')
    //vue2監聽
    // watch(user,({firstName,lastName})=>{
    //     fullName3.value=firstName+'_'+lastName
    // },{immediate:true,deep:true})
    //immediate默認會執行一次watch

    //vue3監聽 不需要配置immediate deep 默認就有了
    watchEffect(()=>{
      fullName3.value=user.firstName+'_'+user.lastName
    })

    //vue3監聽2 下面改變 上面也會跟著改變
    watchEffect(()=>{
      const names=fullName3.value.split('_')
      user.firstName=names[0]
      user.lastName=names[1]
    })


    //watch--可以監視多個數據
    watch([()=>user.firstName,()=>user.lastName,fullName3],()=>{
      //user.firstName user.lastName不適響應式數據 fullName3是響應式(v-model)
      console.log('====')
    })


    return {
      user,
      fullName1,
      fullName2,
      fullName3
    };
  },
});
</script>
