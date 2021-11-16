<template>
  <div>
    <b-list-group-item>
      <span v-if="todo.done" class="done">{{ todo.text }}</span>
      <span v-else>{{ todo.text }}</span>
      <span v-if="todo.done" class="float-right">&#128077;</span>
      <b-button v-else class="float-right" pill variant="outline-success" @click="completeTodo(todo)">&#10003;</b-button>
    </b-list-group-item>
  </div>
</template>

<script>

export default {
  name: 'TodoItem',
  props: {
    todo: {
        type: Object,
        request: true
    }
  },
  methods: {
      completeTodo(todo){
          this.$emit("complete-todo", todo);
      }
  }
}
</script>

<style>
.done{
    text-decoration: line-through;
}
</style>