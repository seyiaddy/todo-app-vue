<template>
  <div>
    <v-list-item>
      <v-list-item-content>
        <v-list-item-title>{{ todo }}</v-list-item-title>
      </v-list-item-content>
      <v-list-item-action >
        <v-btn icon @click="deleteHandler">
          <v-icon>mdi-delete</v-icon>
        </v-btn>

        <!-- Dialog box -->
        <v-dialog v-model="dialog" width="500">
          <template v-slot:activator="{on, attrs}">
            <v-btn icon v-bind="attrs" v-on="on">
              <v-icon>mdi-pencil</v-icon>
            </v-btn>
          </template>

          <v-card>
            <v-card-title class="headline">
              Edit Todo
            </v-card-title>
            <v-card-text>
              <v-container>
                <v-row justify="center">
                  <v-col cols="12" sm="8" md="6">
                    <v-text-field v-model="newTodo">dd</v-text-field>
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

      </v-list-item-action>
    </v-list-item>
  </div>
</template>

<script>
export default {
  name: "Todo",
  data() {
    return {
      dialog: false,
      newTodo: ""
    };
  },
  props: ["todo", "id"],
  methods: {
    deleteHandler() {
      
    },
    updateTodo() {

    }
  },
};
</script>
