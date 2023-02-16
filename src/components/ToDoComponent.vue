<template>
  <h1>Todo List</h1>
  <TodoInputComponent :create="addTodo"/>
  <ToDoListComponent v-if="!isLoad" :todoList="todoList" :checked="checkedTodo" :deleted="deleteTodo"/>
  <SpinnerComponent v-else/>
  <p v-show="!isLoad && todoList.length === 0">Добавьте задачи</p>
</template>

<script>
import TodoInputComponent from "./TodoInputComponent.vue"
import ToDoListComponent from "./ToDoListComponent.vue";
import SpinnerComponent from "./SpinnerComponent.vue";
export default {
  name: "ToDoComponent",
  components: {
    TodoInputComponent,
    ToDoListComponent,
    SpinnerComponent
  },
  data() {
    return {
      todoList: [],
      title: '',
      isLoad: true
    }
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos/?_limit=5&_delay=2100')
        .then(response => response.json())
        .then(json => {
          this.todoList = [...this.todoList, ...json]
          this.isLoad = false
        })
  },
  methods: {
    addTodo(title) {
      const todo = {id: this.getNewId(), title: title, isComplete: false}
      this.todoList.push(todo)
    },
    checkedTodo(id) {
      return this.todoList.map(item => {
        if (item.id === id) item.isComplete = !item.isComplete
      })
    },
    getNewId(){
      return this.todoList.length > 0 ? this.todoList[this.todoList.length - 1].id + 1 : 0;
    },
    deleteTodo(index) {
      return this.todoList.splice(index, 1)
    }
  }
}
</script>

<style lang="scss" scoped>

</style>