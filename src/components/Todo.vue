<template>
  <div>
    <v-list-item>
      <v-list-item-content>
        <v-list-item-title>{{ todo }}</v-list-item-title>
      </v-list-item-content>
      <v-list-item-action>
        <div>
        <!-- Dialog box -->
        <v-dialog v-model="dialog" width="500">
          <template v-slot:activator="{ on, attrs }">
            <v-btn icon v-bind="attrs" v-on="on" class="float-left">
              <v-icon color="primary">mdi-pencil</v-icon>
            </v-btn>
          </template>

          <v-card>
            <v-card-title class="headline">
              Edit Todo
            </v-card-title>
            <v-card-text>
              <v-container>
                <v-row justify="center">
                  <v-col cols="12">
                    <v-text-field
                      label="Enter new value"
                      @keyup.enter="updateTodo"
                      v-model="newTodo"
                    ></v-text-field>
                  </v-col>
                </v-row>
              </v-container>
            </v-card-text>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn @click="dialog = false">
                Cancel
              </v-btn>
              <v-btn @click="updateTodo">
                Save
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
        <!-- Dialog box  -->

        <v-btn icon @click="deleteTodo">
          <v-icon color="error">mdi-delete</v-icon>
        </v-btn>
        </div>
      </v-list-item-action>
    </v-list-item>
  </div>
</template>

<script>
import db from "../plugins/firebase";

export default {
  name: "Todo",
  data() {
    return {
      dialog: false,
      newTodo: this.todo,
    };
  },
  props: ["todo", "id"],
  methods: {
    deleteTodo() {
      db.collection("todos")
        .doc(this.id)
        .delete();
    },
    updateTodo() {
      db.collection("todos")
        .doc(this.id)
        .update({
          todo: this.newTodo,
        });

      this.dialog = false;
    },
  },
};
</script>
