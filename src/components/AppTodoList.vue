<template>
  <ul class="todo-list">
    <AppTodoItem v-for="todo in todos" :todo="todo" :key="todo.id" 
      @toggleTodoComplete="toggleTodo"
      @deleteTodo="deleteTodo" />
  </ul>
</template>
<script lang="ts">
import { defineComponent, PropType } from 'vue';
import AppTodoItem from './AppTodoItem.vue';
import { Todo } from '@/models/Todo';

export default defineComponent({
  components: {
    AppTodoItem,
  },
  props: {
    todos: {
      type: Array as PropType<Todo[]>,
        required: true
    }
  },
  methods: {
    toggleTodo(id: number) {
      this.$emit("toggleTodo", id)
    },
    deleteTodo(id: number) {
      this.$emit("deleteTodo", id)
    }
  },
  emits:{
    toggleTodo: (id:number)=> Number.isInteger(id),
    deleteTodo: (id:number)=> Number.isInteger(id)
  }
})

</script>