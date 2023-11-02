<template>
  <ul class="todo-list">
    <AppTodoItem v-for="todo in todos" :todo="todo" :key="todo.id"/>
  </ul>
</template>
<script lang="ts">
import { defineComponent } from 'vue';
import AppTodoItem from './AppTodoItem.vue';
import { Todo } from '@/models/Todo';

interface State {
  todos: Todo[];
}

export default defineComponent({
  components: {
    AppTodoItem,
  },
  data(): State {
    return {
      todos: [
        {id: 0, text:'Learn the basics of Vue', completed: true},
        {id: 1, text:'Learn the basics of Typescript', completed: false},
        {id: 2, text:'Subscribe to the channel', completed: false},
      ]
    }
  }
})

</script>