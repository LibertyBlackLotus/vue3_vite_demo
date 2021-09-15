<template>
    <div>
        <p>{{state}}</p>
        <button @click="myFn1">click</button>

        <hr />
        <p>{{state2}}</p>
        <button @click="myFn2">click</button>
    </div>
</template>

<script>
import { reactive, toRaw, ref } from 'vue'
export default{
    setup(){ // composition api 本质是把setup中的数据和方法注入到组件中
        let obj = { name: 'wanglin', age: 18}  
        let state = reactive(obj) //这里state 本质是一个Proxy对象，在这个Proxy对象中引用了obj
        let state2 = ref(obj)
        let obj2 = toRaw(state)  //不需要实时更新数据时使用此方法获得原始值
        console.log(obj === obj2)  //true

        let obj3 = toRaw(state2.value)  //获取rer原始值，需要获取value属性
        console.log(state2) 
        console.log(obj3) 

        function myFn1(){
            obj.name = 'lin'  //直接修改obj，无法触发state在UI的更新 
            console.log(obj);
            console.log(state2);
        }

        function myFn2(){
            obj.name = 'lin' 
        }

        return { state, myFn1, state2, myFn2 }
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
