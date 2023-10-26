<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
  },
  methods: {
    toggleCheckbox(e) {
      this.$emit("toggle-checkbox", {
        id: this.todo.id,
        checked: e.target.checked,
      });
    },
    clickDelete() {
      this.$emit("click-delete", this.todo.id);
    },
  },
};
</script>
<template>
  <div class="form-check" :data-id="todo.id">
    <input
      class="form-check-input"
      type="checkbox"
      value=""
      :id="'input' + todo.id"
      @change="toggleCheckbox" />
    <label
      class="form-check-label"
      :for="`input${todo.id}`"
      :style="{
        'text-decoration': todo.checked ? 'line-through' : 'none',
        color: todo.checked ? 'red' : 'black',
      }">
      {{ todo.text }}
    </label>
    <button
      type="button"
      class="btn btn-danger btn-sm ms-2"
      @click="clickDelete">
      X
    </button>
  </div>
</template>
