<template >
  <AppHeader />
  <AppFilters :selectedFilter="filter" @select-filter="selectFilter" />
  <main class="app-main">
    <AppTodoList :todos="filteredTodos" @toggle-todo="toggleTodo" @delete-todo="deleteTodo" />
    <AppNewTodo @add-todo="addTodo" />
  </main>
  <AppFooter :stats="stats"/>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import AppFilters from './components/AppFilters.vue';
import AppHeader from './components/AppHeader.vue';
import AppTodoList from './components/AppTodoList.vue';
import AppNewTodo from './components/AppNewTodo.vue';
import AppFooter from './components/AppFooter.vue';
import { Todo } from './models/Todo';
import { FilterType } from './models/FilterType';
import { Stats } from './models/Stats';

interface State {
  todos: Todo[];
  filter: FilterType;
}

export default defineComponent({
  components: {
    AppHeader,
    AppFilters,
    AppTodoList,
    AppNewTodo,
    AppFooter,
  },
  data(): State {
    return {
      todos: [
        { id: 0, text: 'Learn the basics of Vue', completed: true },
        { id: 1, text: 'Learn the basics of Typescript', completed: false },
        { id: 2, text: 'Subscribe to the channel', completed: false },
      ],
      filter: FilterType.All
    }
  },
  computed: {
    activeTodos(): Todo[]{
      return this.todos.filter(todo => !todo.completed);
    },
    doneTodos(): Todo[]{
      return this.todos.filter(todo => todo.completed);
    }, 
    filteredTodos(): Todo[] {
      switch (this.filter) {
        case FilterType.Active:
          return this.activeTodos;
        case FilterType.Done:
          return this.doneTodos;
        case FilterType.All:
        default:
          return this.todos;
      }
    },
    stats(): Stats {
      if (this.todos.length) {
        return {
          active: this.activeTodos.length,
          done: this.doneTodos.length
        }
      }
      return {
        active: 0, done: 0
      }

    }
  },
  methods: {
    toggleTodo(id: number) {
      let updatedTodo = this.todos.find((todo: Todo) => todo.id === id);
      if (updatedTodo) {
        updatedTodo.completed = !updatedTodo.completed;
      }
    },
    deleteTodo(id: number) {
      this.todos = this.todos.filter((todo: Todo) => todo.id !== id);
    },
    addTodo(todo: Todo) {
      this.todos.push(todo);
    },
    selectFilter(filter: FilterType) {
      this.filter = filter;
    }
  }
})
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
