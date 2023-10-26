<script>
import Todo from "./components/Todo.vue";
export default {
  components: {
    Todo,
  },
  data() {
    return {
      todoText: "",
      todos: [
        { id: 1, text: "Learn web", checked: false },
        { id: 2, text: "Get a job", checked: false },
        { id: 3, text: "Study Hard", checked: false },
      ],
    };
  },
  methods: {
    AddTodo(e) {
      // console.log(e.target.value);
      this.todos.push({
        id: Math.random(),
        text: e.target.value,
        checked: false,
      });
      this.todoText = "";
    },
    toggleCheck({ id, checked }) {
      const index = this.todos.findIndex((todo) => todo.id === id);
      this.todos[index].checked = checked;
      console.log(this.todos);
    },
    deleteTodo(id) {
      if (window.confirm("정말 삭제할까요")) {
        const index = this.todos.findIndex((todo) => todo.id === id);
        this.todos.splice(index, 1);
      } else {
        alert("취소되었습니다.");
      }
    },
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
        placeholder="할일을 입력하세요"
        required
        @keyup.enter="AddTodo"
        v-model="todoText" />
    </div>
    <Todo
      v-for="todo in todos"
      key="todo.id"
      :todo="todo"
      @toggle-checkbox="toggleCheck"
      @click-delete="deleteTodo" />
  </div>
</template>

<style scoped>
#app {
  display: grid;
  grid-template-columns: 1fr;
  padding: 0 2rem;
}
</style>
