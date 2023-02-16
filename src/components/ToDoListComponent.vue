<template>
  <div class="todo">
    <ul class="todo-list">
      <li class="todo-item" v-for="(todo, index) in todoList">
        <ToDoItemComponent :key="todo.id" :todo="todo" :index="index" :checked="checkTodo" :deleted="deletedTodo"/>
      </li>
    </ul>

  </div>
</template>

<script>
import ToDoItemComponent from "./ToDoItemComponent.vue";
export default {
  name: "ToDoListComponent",
  components: {
    ToDoItemComponent,
  },
  props: ['todoList', 'checked', 'deleted'],
  methods: {
    checkTodo(id) {
      this.checked(id)
    },
    deletedTodo(index) {
      this.deleted(index)
    }
  }
}
</script>

<style scoped lang="scss">
.todo-list {
  margin: 0;
  padding: 0;
}
.todo-item {
  display: flex;
  align-items: center;
  justify-content: flex-start;
}
</style>