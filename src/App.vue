<template>
  <v-app>
    <h1>Todo App</h1>
    <v-container>
      <v-row align="center" justify="space-between">
        <v-col md="4">
          <v-text-field label="Enter Todo" @keypress.enter="clickHandler" />
        </v-col>
        <v-col md="8">
          <v-btn depressed elevation="1" @click="clickHandler">Add Todo</v-btn>
        </v-col>
      </v-row>
      <v-list>
      <Todo />
      </v-list>
    </v-container>
  </v-app>
</template>

<script>
import Todo from "./components/Todo";

export default {
  name: "App",
  components: {
    Todo
  },
  data() {
    return {

    }
  },
  methods: {
    clickHandler() {
      alert("hey")
    }
  }
};
</script>

<style scoped>
* {
  text-align: center;
}
</style>
