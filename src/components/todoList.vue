<template>
  <li>
    <button @click="$emit('done', todo.id)">x</button>
    <p>{{ todo.text }}</p>
  </li>
</template>

<script>
export default {
  name: "todoList",
  props: {
    todo: {
      type: Object,
      required: true
    }
  }
};
</script>
