<template>
  <div>
    <ul class="todolist" v-for="todo,index in state.todoList" :key="todo.todo">
      <li >{{ todo.todo }}:{{ index }}</li>
      <button @click="deleteTodoAction(index)">削除</button>
    </ul>
    <Todo-input @add-todo="addTodoAction" />
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive } from "vue";
import TodoInput from "../components/TodoInput.vue";

export default defineComponent({
  name: "TodoList",
  components: {
    TodoInput,
  },

  setup() {
    const state = reactive<{ todoList: Array<{ todo: string }> }>({
      todoList: []
    });
    const addTodoAction = (value:string)=>{
      state.todoList.push({todo:value})
    }
    const deleteTodoAction = (index: number) => {
      console.log(index)
      state.todoList.splice(index,1)
    }
    return { state,addTodoAction,deleteTodoAction };
  },
});
</script>

<style></style>
