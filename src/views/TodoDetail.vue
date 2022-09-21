<template>
  <h3>{{ todo.detail }}</h3>
  <button @click="homeBtn">Home</button>
</template>

<script>
export default {
  props: ["id"],
  data() {
    return {
      todo: [],
    };
  },
  mounted() {
    fetch("http://localhost:3000/todos/" + this.id)
      .then((res) => res.json())
      .then((data) => (this.todo = data))
      .catch((err) => console.log(err.message));
  },
  methods: {
    homeBtn() {
      this.$router.push({ name: "home" });
    },
  },
};
</script>

<style>
</style>