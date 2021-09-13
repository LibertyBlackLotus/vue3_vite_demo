<template>
    <div>
        <p>{{username}}</p>
        <button @click="myFn1">click</button>

        <p>{{age}}</p>
        <button @click="myFn2">click</button>
    </div>
</template>

<script>
import { ref } from 'vue'
export default{
    data(){
        return {
            username: 'wanglin'
        }
    },

    //option api
    methods: {
        myFn1(){
            alert('abc')
        }
    },

    /* 
    1、setup 执行时机：
    在beforeCretead与created之间执行
    2、注意点：
    - 在setup中无法访问data和methods
    - setup中的this为undefined
    - setup是同步的，不能是异步函数
    */
    setup(){ // composition api 本质是把setup中的数据和方法注入到组件中
        let age = ref(18)
        function myFn2(){
            alert('my fn2')
        }

        return { age, myFn2 }
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
