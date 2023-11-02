<template >
  <AppHeader />
  <AppFilters />
  <main class="app-main">
    <AppTodoList />
    <AppNewTodo />
  </main>
  <AppFooter />
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import AppFilters from './components/AppFilters.vue';
import AppHeader from './components/AppHeader.vue';
import AppTodoList from './components/AppTodoList.vue';
import AppNewTodo from './components/AppNewTodo.vue';
import AppFooter from './components/AppFooter.vue';

export default defineComponent({
  components: {
    AppHeader,
    AppFilters,
    AppTodoList,
    AppNewTodo,
    AppFooter,
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
