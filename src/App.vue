<script>
export default {
  data() {
    return {
      todoText: "",
      todos: [
        { id: 1, text: "Learn web", checked: false },
        { id: 2, text: "Get a job", checked: false },
      ],
    };
  },
};
</script>

<template>
  <div class="container">
    <h1 class="text-center">Todo App</h1>
    <div class="mb-3">
      <label for="todo" class="form-label">Todo Input</label>
      <input
        type="text"
        class="form-control"
        id="todo"
        placeholder="할일을 입력하세요" />
    </div>
  </div>
</template>

<style scoped>
#app {
  display: grid;
  grid-template-columns: 1fr;
  padding: 0 2rem;
}
</style>
