<template>
  <section class="main">
    <input id="toggle-all" class="toggle-all" type="checkbox" />
    <label for="toggle-all">Mark all as complete</label>
    <ul class="todo-list">
      <li :class="{completed:item.done}" v-for="item in list" :key="item.id">
        <div class="view">
          <!--:checked="item.done 动态绑定选中状态  -->
          <input @change="change(item.id)" class="toggle" type="checkbox" :checked="item.done" />
          <label>{{item.name}}</label>
          <button @click="delTodo(item.id)" class="destroy"></button>
        </div>
        <input class="edit" value="Create a TodoMVC template" />
      </li>
      <!-- <li>
        <div class="view">
          <input class="toggle" type="checkbox" />
          <label>Buy a unicorn</label>
          <button class="destroy"></button>
        </div>
        <input class="edit" value="Rule the web" />
      </li> -->
    </ul>
  </section>
</template>

<script setup>
  //接收子组件传递过来的数组
    defineProps({
      list:{
        type: Array,
        //默认给个空数组
        default: ()=>[]
      }
    })
    //定义emit方法
    const emit = defineEmits(['changeTask','delTask'])
    // 触发父组件绑定的自定义事件
    const change=(id)=>{
      emit('changeTask',id)
    }
    // 触发父组件绑定的自定义事件,来进行删除操作
    const delTodo=(id)=>{
      emit('delTask',id)
    }
</script>
<style lang="less" scoped></style>
