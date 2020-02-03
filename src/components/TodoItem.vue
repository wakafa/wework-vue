<template>
  <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
    <p id="todo-item-title">
      <button class="completed-switch" v-show="!todo.completed" @click="completedSwitch">&#9989;</button>
      <button class="completed-switch" v-show="todo.completed" @click="completedSwitch">&#10062;</button>
      {{todo.title}}
      <button
        class="del-button"
        v-show="todo.completed"
        @click="$emit('del-todo', todo.id)"
      >&#10060;</button>
    </p>
    <p id="todo-item-content">{{todo.content}}</p>
    <div class="edit" v-show="!todo.completed">
    <input v-model="todo.content" placeholder="todo content" />
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    completedSwitch() {
      this.todo.completed = !this.todo.completed;
    }
  }
};
</script>


<style scoped>
.todo-item {
  background: #f4f4f4;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
}

#todo-item-title {
  background-color: rgb(226, 189, 189);
  font-size: 150%;
}

#todo-item-content {
  background-color: rgb(192, 143, 38);
  font-family: "Courier New", Courier, monospace;
}
.is-complete {
  text-decoration: line-through;
}

.del-button {
  color: #fff;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
</style>