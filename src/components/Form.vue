<template>
  <v-app>
    <v-container>
      <v-text-field
        v-on:addnewTodo.prevent
        label="Add new ToDo"
        v-model="text"
        :rules="rules"
        hide-details="auto"
        v-on:keypress="addnewTodo"
        v-on:click="addnewTodo"
      ></v-text-field>
    </v-container>
  </v-app>
</template>
<script>
export default {
  name: "App",

  components: {},

  data: () => ({
    text: "",
    rules: [
      (value) => !!value || "Required.",
      (value) => (value && value.length >= 3) || "Min 3 characters",
    ],
  }),
  methods: {
    addnewTodo() {
      //   if (e.keyCode === 13) {
      //     if (this.editIndex !== -1) {
      //       if (this.text.length !== 0) {
      //         this.$emit("edit-item", {
      //           name: this.text,
      //           editIndex: this.editIndex,
      //         });
      //       }
      //     } else {
      //       this.$emit("submit-item", this.text);
      //     }
      //     this.text = "";
      //   }
      if ((this.text === "")) {
          console.log("Hiiiii")
      }
    },
  },
};
</script>
