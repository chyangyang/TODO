<template>
  <header class="header">
    <h1>todos</h1>
    <input @keydown.enter="hKeydown" v-model="taskname" class="new-todo" placeholder="你想做点什么?" autofocus />
  </header>
</template>
<script setup>
import { ref } from 'vue';
//定义一个任务名称
const taskname=ref('')
const emit=defineEmits(['add'])
const hKeydown=()=>{
  // 进行非空判断
  if (taskname.value.length===0) return
  emit('add',taskname.value)
  //清空输入框
  taskname.value=''
}
</script>
<style lang="less" scoped></style>
