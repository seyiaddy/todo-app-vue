<template>
  <v-app class="app">
    <h1 class="text-center">Todo App</h1>
    <v-container>
      <v-form>
        <v-row justify="center">
          <v-spacer></v-spacer>
          <v-col cols="12" sm="6">
            <v-text-field label="Enter Todo" v-model="input" />
          </v-col>
          <v-col cols="12" sm="4" class="text-center text-sm-left">
            <v-btn type="submit" depressed elevation="1" @click="clickHandler">Add Todo</v-btn>
          </v-col>
        </v-row>
      </v-form>
      <ul>
        <v-list v-for="todo in todos" :key="todo.id">
          <Todo :id="todo.id" :todo="todo.todo" class="list-item" />
        </v-list>
      </ul>
    </v-container>
  </v-app>
</template>

<script>
import Todo from "./components/Todo";
// import db from "./plugins/firebase";
// import firebase from "firebase";

export default {
  name: "App",
  components: {
    Todo
  },
  data() {
    return {
      input: "",
      todos: [{
        id: 3,
        todo: "Hello"
      },
      {
        id: 1,
        todo: "はじめまして"
      }]
    }
  },
/*   mounted() {
      db.collection("todos").orderBy("timstamp", "desc").onSnapshot(snapshot => {
        this.todos.push(snapshot.docs.map(doc => ({id: doc.id, todo: doc.data().todo})));
      });
  }, */
  methods: {
    clickHandler(e) {
      e.preventDefault();

    },
  }
};
</script>

<style>
.app {
  margin-top: 20px;
}
</style>
