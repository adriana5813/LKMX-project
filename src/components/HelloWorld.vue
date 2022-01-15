<template>
  <center><div class="wrapper">
    <h1>To Do List</h1>
    <form>
      <input
        type="text"
        name="todo-text"
        v-model="newTodoText"
        placeholder="Escribe una tarea"       
      />
      <button @click.prevent="addTodo">Agregar</button>
    </form>
    <ul v-if="todos.length">
      <TodoItem
        v-for="todo in todos"
        :key="todo.id"
        :todo="todo"
        @remove="removeTodo"
        @edit="editTodo"
      />
    </ul>
    <p class="none" v-else>No has agregado tareas.</p>
  </div></center>
</template>

<script>
import TodoItem from "./TodoItem.vue";

let nextTodoId = 1;

const createTodo = (text) => ({
  text,
  id: nextTodoId++,
});

export default {
  components: {
    TodoItem,
  },

  data() {
    return {
      todos: [],

      newTodoText: "",
    };
  },

  methods: {
    addTodo() {
      const trimmedText = this.newTodoText.trim();

      if (trimmedText) {
        this.todos.push(createTodo(trimmedText));
      }

      this.newTodoText = "";
    },

    removeTodo(item) {
      this.todos = this.todos.filter((todo) => todo !== item);
    },
    editTodo(item) {
      var objIndex = this.todos.findIndex((obj) => obj.id == item.id);
      this.todos[objIndex].text = "";
    },
  },
};
</script>

<style >
.wrapper {
  border-radius: 5px;
  background-color: #f2f2f2;
  padding: 10px;
  width: 40%;
}
h1{
    text-align: left;
}
input{
    width: 80%;
    text-align: left;
}
button{
    background-color: cornflowerblue;
    border: none;
    margin-left:5px;
    font-size: 15px;
    border-radius: 3px;
    color: white;
}
form{
    width: 100%;
}
</style>

