<template>
  <div>
    <b-container>
      <b-row>
        <b-col>
          <TodoList />
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import TodoList from '@/compomemts/TodoList'

export default {
  name: 'App',
  components: {
    TodoList
  }
}
</script>

<style>
</style>