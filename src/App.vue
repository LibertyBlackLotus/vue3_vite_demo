<template>
    <div>
        <p>{{state}}</p>
        <button @click="myFn1">click</button> 
    </div>
</template>

<script>
import { reactive, markRaw } from 'vue'
export default{
    setup(){ // composition api 本质是把setup中的数据和方法注入到组件中
        let obj = { name: 'wanglin', age: 18}  
        obj = markRaw(obj) //ojb将不会响应式
        let state = reactive(obj) //这里state 本质是一个Proxy对象，在这个Proxy对象中引用了obj 

        function myFn1(){
            state.name = 'lin'  //直接修改obj，无法触发state在UI的更新 
        }

        return { state, myFn1 }
    }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
