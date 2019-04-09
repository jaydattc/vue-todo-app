<template>
  <li>
    <div v-show="!todo.editMode" class="todo">
      <button @click="$emit('done', todo.id)">❎</button>
      <p>{{ todo.text }}</p>
      <button @click="todo.editMode = true">
        {{ todo.editMode ? done : edit }}
      </button>
    </div>
    <div v-show="todo.editMode" class="edit">
      <input type="text" class="edit" v-model="todo.text" />
      <button @click="todo.editMode = false">
        {{ todo.editMode ? done : edit }}
      </button>
    </div>
  </li>
</template>

<script>
export default {
  name: "todoList",
  data: function() {
    return { edit: "✏️", done: "✅" };
  },
  props: {
    todo: {
      type: Object,
      required: true
    }
  },
  computed: {}
};
</script>
