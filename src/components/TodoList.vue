<template>
  <div>
    <Todo
      v-for="item in todos"
      :key="item.key"
      :todo="item"
      @deleteHandler="$emit('deleteHandler', $event)"
      @saveEdit="$emit('saveEdit', $event)"
    />
  </div>
</template>

<script>
import Todo from "./Todo.vue";
export default {
  components: { Todo },
  emit: ["deleteHandler", "saveEdit"],
  props: {
    todos: {
      type: Array,
      require: true,
    },
  },
  methods: {},
};
</script>

<style>
</style>