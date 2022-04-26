<script setup lang="ts">

import { genTodoId } from '../../service/todoData'
import { ref } from 'vue';

let title = ref('')

const emit = defineEmits(['addTodo'])

function addTodo() {
  const newTodo = {
    id: genTodoId(),
    title: title.value,
    completed: false,
  }
  emit('addTodo', newTodo)
  title.value = '';
}

</script>

<template>
  <div>
    <form @submit.prevent="addTodo()">
      <input type=" text" name="title" v-model="title" placeholder="Add Todo....." />
      <input type="submit" value="submit" class="btn" />
    </form>
  </div>
</template>

<style scoped>
form {
  display: flex;
}

input[type="text"] {
  flex: 10;
  padding: 5px;
}

input[type="submit"] {
  flex: 2;
}
</style>