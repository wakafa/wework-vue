<template>
  <div id="app">
    <button class="btn btn-hide-show" v-on:click="toggleSeen">{{ button.text }}</button>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Todos from "./components/Todos";

export default {
  name: "app",
  components: {
    Todos
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: "First todo",
          content: "Content First",
          completed: false
        },
        {
          id: 2,
          title: "Second todo",
          content: "Content Second",
          completed: true
        },
        {
          id: 3,
          title: "Third todo",
          content: "Content Third",
          completed: false
        },
        {
          id: 4,
          title: "Pick up grandma",
          content: "from the airport",
          completed: true
        },
        {
          id: 5,
          title: "Go for a walk",
          content: "at least 5km",
          completed: false
        }
      ],
      button: {
        text: "Hide my todos"
      },
      seen: true
    };
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    toggleSeen() {
      this.seen = !this.seen;
      this.button.text = this.seen ? "Hide my todos" : "Show my todos";
      let display = this.seen ? "block" : "none";
      document.getElementsByClassName("todo-item").forEach(elem => {
        elem.style.display = display;
      });
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

.btn-hide-show {
  margin: 100px;
  background-color: gray;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
</style>
