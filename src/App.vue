<template>
  <div id="app">
    <h3>{{title}}</h3>
    <form @submit.prevent="addTodo">
      <label for="newTodo">New Todo</label>
      <input
        @enter.prevent="addTodo"
        v-model="newTodo"
        type="text"
        name="newTodo"
        id="newTodo"
        value
      >
      <button type="submit" name="button">Add</button>
    </form>
    <button @click="allDone" type="button" name="button">All Done</button>
    <ul>
      <li v-for="todo in todos" :key="todo.title">
        <span>{{todo.title}}</span>
        <button @click="removeTodo(todo)" type="button" name="button">Remove</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "app",

  data() {
    return {
      title: "Todo App",
      newTodo: "",
      todos: []
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo === "") {
        return alert("Fill the input");
      }
      this.todos.push({
        title: this.newTodo
      });
      this.newTodo = "";
    },
    removeTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex, 1);
    },
    allDone() {
      this.todos.forEach(todo => {
        todo.done = true;
      });
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
