<template>
  <v-list-item>
    <v-list-item-content>
      <v-list-item-title>List item</v-list-item-title>
    </v-list-item-content>
    <v-list-item-action>
      <v-btn icon>
        <v-icon>mdi-delete</v-icon>
      </v-btn>
      <v-btn icon>
        <v-icon>mdi-pencil</v-icon>
      </v-btn>
    </v-list-item-action>
  </v-list-item>
</template>

<script>
export default {
  name: "Todo",
};
</script>
