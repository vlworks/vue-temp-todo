<template>
  <div class="todo-create">
    <form class="todo-create-form" @submit.prevent="addTodo">
      <input class="todo-create__input" type="text" placeholder="Введите название задачи" v-model="title">
      <input class="todo-create__submit" type="submit" value="Добавить">
    </form>
  </div>
</template>

<script>
export default {
  name: "TodoInputComponent",
  props: ['create'],
  data() {
    return {
      title: ""
    }
  },
  methods: {
    addTodo() {
      this.create(this.title)
      this.title = ''
    }
  }
}
</script>

<style scoped>

</style>