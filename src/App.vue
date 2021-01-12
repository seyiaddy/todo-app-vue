<template>
  <v-app class="app">
    <v-app-bar app flat color="white" outlined>
      <h1>Todo App</h1>
    </v-app-bar>

    <v-main>
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
    </v-main>
  </v-app>
</template>

<script>
import Todo from "./components/Todo";
import db from "./plugins/firebase";
import firebase from "firebase";

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
  created() {
    this.populateTodos();
  },
  methods: {
    clickHandler(e) {
      e.preventDefault();

      db.collection("todos").add({
        todo: this.input,
        timestamp: firebase.firestore.FieldValue.serverTimestamp()
      }).then(() => {
        this.populateTodos();
      })

      this.input = "";
    },
    populateTodos() {
      db.collection("todos").orderBy("timestamp", "desc").onSnapshot(snapshot => {
      this.todos = snapshot.docs.map(doc => ({id: doc.id, todo: doc.data().todo}))
    }, (error) => {alert(`An error occured: ${error}`)});
    }
  }
};
</script>

<style>
.app {
  margin-top: 20px;
}
</style>
