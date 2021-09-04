<template>
  <div id="app">
    <AddTodo @addTodo="addTodo" />
    <TodoList
      :todos="todos"
      @deleteHandler="deleteHandler"
      @saveEdit="saveEdit"
    />
  </div>
</template>

<script>
import AddTodo from "./components/AddTodo.vue";
import TodoList from "./components/TodoList.vue";

export default {
  components: { TodoList, AddTodo },
  name: "App",
  data() {
    return {
      todos: [
        // {
        //   key: 1,
        //   done: false,
        //   text: "Read a book",
        // },
        // {
        //   key: 2,
        //   done: true,
        //   text: "Go to gym",
        // },
        // {
        //   key: 3,
        //   done: false,
        //   text: "Do home work",
        // },
      ],
    };
  },
  methods: {
    addTodo(text) {
      this.todos.push({
        text,
        key: Date.now(),
        done: false,
      });
    },
    deleteHandler(key) {
      this.todos = this.todos.filter((item) => item.key !== key);
    },
    saveEdit({ key, text }) {
      this.todos = this.todos.map(item => {
        if (item.key == key) {
          return {
            ...item,
            text: text,
          };
        }
        return item;
      });
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
