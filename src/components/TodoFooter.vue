<script setup>
import { computed } from 'vue';

const {list} = defineProps({
  list:{
    type:Array,
    required:true
  }
})
// 定义计算属性
const leftCount=computed(()=>list.filter(item=>!item.done).length)
</script>
<template>
  <footer class="footer">
    <span class="todo-count"><strong>{{leftCount}}</strong> item left</span>
    <ul class="filters">
      <li>
        <a class="selected" href="#/">All</a>
      </li>
      <li>
        <a href="#/active">Active</a>
      </li>
      <li>
        <a href="#/completed">Completed</a>
      </li>
    </ul>
    <button class="clear-completed">Clear completed</button>
  </footer>
</template>

<style lang="less" scoped></style>
