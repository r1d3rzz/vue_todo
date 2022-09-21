<template>
  <div v-for="todo in todos" :key="todo.id">
    <router-link :to="{ name: 'todoDetail', params: { id: todo.id } }">
      <h3>{{ todo.body }}</h3>
    </router-link>
  </div>
</template>

<script>
export default {
  data() {
    return {
      todos: [],
    };
  },
  mounted() {
    fetch("http://localhost:3000/todos")
      .then((res) => res.json())
      .then((data) => (this.todos = data))
      .catch((err) => console.log(err.message));
  },
};
</script>

<style>
</style>