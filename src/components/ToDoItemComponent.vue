<template>
  <div class="todo-item-desc">
    <input type="checkbox" :name="todo.id" :id="todo.id" :checked="todo.isComplete" @change="changeTodo(todo.id)">
    <label :for="todo.id" :class="{done: todo.isComplete}">{{ todo.title }}</label>
  </div>
  <div class="todo-item__delete">
    <button class="todo-item__delete-btn" @click="deleteTodo(index)">x</button>
  </div>
</template>

<script>
export default {
  name: "ToDoItemComponent",
  props: ['todo', 'index', 'checked', 'deleted'],
  methods: {
    changeTodo(id) {
      this.checked(id)
    },
    deleteTodo(index) {
      this.deleted(index)
    }
  }
}
</script>

<style scoped lang="scss">
.todo-item {

  &__delete {
    margin-left: auto;
  }
}

.done {
  text-decoration: line-through;
}
</style>