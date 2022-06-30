<template>
  <section class="todoapp">
    <TodoHeader @add="addTask"></TodoHeader>
    <TodoMain @delTask="delTask" :list="list" @change-Task="changeTask"></TodoMain>
    <TodoFooter :list="list"></TodoFooter>
  </section>
</template>
<script setup>
// ref 和 reactive的区别
// 作用：都可以为数据提供响应式的功能
//区别：ref可以为基本数据类型提供，而reactive只能给引用数据类型提供
// 原理：reactive是对对象进行代理，而 ref 是在数据的外面包裹了一层对象，其中.value就是要的数据，
// 整个外层对象进行代理
// Vue3 响应式的原理是采用Proxy进行对象代理，这个代理只能针对对象
import { ref } from 'vue';
//导入组件
import TodoHeader from './components/TodoHeader.vue'
import TodoMain from './components/TodoMain.vue'
import TodoFooter from './components/TodoFooter.vue'
//提供初始数据
const list = ref([
  {id: 1,name: '吃饭',done: true},
  {id: 2,name: '睡觉',done: false},
  {id: 3,name: '打豆豆',done: false}
])
//传入id,改变状态
const changeTask=(id)=>{
  // console.log('当前点击的id是',id);
  // find 找到对应的元素
 const todo = list.value.find(item => item.id === id)
 //状态取反
  todo.done = !todo.done
}
// 进行删除操作
const delTask=(id)=>{
    console.log('当前点击的id是',id);
    //进行过滤覆盖完成删除操作
 list.value=list.value.filter(item=>item.id!==id)
}
//添加操作
//在todoheader进行双向绑定
// 绑定键盘按下事件，把输入的内容传递给父组件
// 在父组件添加数据
const addTask=(taskname)=>{
  console.log(taskname);
  //添加数据
  list.value.push({
    id:Date.now(),
    name:taskname,
    done:false
  })
}
</script>
<style lang="less" scoped></style>
