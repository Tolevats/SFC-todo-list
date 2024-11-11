<template>
  <div id="app">
    <TodoList />

    <footer>
      <p>Tolevats &copy; Copyright 2024</p>
    </footer>
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue';



export default {
  name: 'App',
  components: {
    TodoList
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  margin-top: 60px;
}
footer {
  margin-top: 10rem;
  font-size: 0.75rem;
  font-weight: bolder;
  font-style: italic;
  text-align: center;
}
</style>
