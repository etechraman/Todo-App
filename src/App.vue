<template>
  <v-app>
    <!-- <v-app-bar app color="primary" dark>
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
          transition="scale-transition"
          width="40"
        />

        <v-img
          alt="Vuetify Name"
          class="shrink mt-1 hidden-sm-and-down"
          contain
          min-width="100"
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-name-dark.png"
          width="100"
        />
      </div>

      <v-spacer></v-spacer>

      <v-btn
        href="https://github.com/vuetifyjs/vuetify/releases/latest"
        target="_blank"
        text
      >
        <span class="mr-2">Latest Release</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar> -->

    <v-container>
      <!-- <v-text-field
        label="Add new ToDo"
        v-model="text"
        :rules="rules"
        hide-details="auto"
        v-on:keypress="addnewTodo"
      ></v-text-field> -->
      <Form/>

      <v-list three-line>
        <template v-for="(item, index) in items">
          <v-subheader
            v-if="item.header"
            :key="item.header"
            v-text="item.header"
          ></v-subheader>

          <v-divider
            v-else-if="item.divider"
            :key="index"
            :inset="item.inset"
          ></v-divider>

          <v-list-item v-else :key="item.title">
            <v-list-item-content>
              <v-list-item-title v-html="item.title"> </v-list-item-title>
              <v-list-item-subtitle
                v-html="item.subtitle"
              ></v-list-item-subtitle>
            </v-list-item-content>

            <v-btn class="mx-2" fab dark large color="cyan" @click="edit(item.title)">
              <v-icon dark>
                mdi-pencil
              </v-icon>
            </v-btn>
          </v-list-item>
        </template>
      </v-list>

      <!-- <v-btn class="mx-2" fab dark large color="cyan">
        <v-icon dark>
          mdi-pencil
        </v-icon>
      </v-btn> -->
    </v-container>

    <v-main> </v-main>
  </v-app>
</template>

<script>
import Form from './components/Form'
export default {
  name: "App",

  components: {
    Form
  },

  data: () => ({
    text: "",
    temp: {
      title: "",
      subtitle: `<span class="text--primary">Ali Connors</span> &mdash; I'll be in your neighborhood doing errands this weekend. Do you want to hang out?`,
    },
    items: [
      { header: "Today" },
      {
        title: "Brunch this weekend?",
        subtitle: `<span class="text--primary">Ali Connors</span> &mdash; I'll be in your neighborhood doing errands this weekend. Do you want to hang out?`,
      },
      { divider: true, inset: true },
      {
        title: 'Summer BBQ <span class="grey--text text--lighten-1">4</span>',
        subtitle: `<span class="text--primary">to Alex, Scott, Jennifer</span> &mdash; Wish I could come, but I'm out of town this weekend.`,
      },
      { divider: true, inset: true },
      {
        title: "Oui oui",
        subtitle:
          '<span class="text--primary">Sandra Adams</span> &mdash; Do you have Paris recommendations? Have you ever been?',
      },
      { divider: true, inset: true },
      {
        title: "Birthday gift",
        subtitle:
          '<span class="text--primary">Trevor Hansen</span> &mdash; Have any ideas about what we should get Heidi for her birthday?',
      },
      { divider: true, inset: true },
      {
        title: "Recipe to try",
        subtitle:
          '<span class="text--primary">Britta Holt</span> &mdash; We should eat this: Grate, Squash, Corn, and tomatillo Tacos.',
      },
    ],
    rules: [
      (value) => !!value || "Required.",
      (value) => (value && value.length >= 3) || "Min 3 characters",
    ],
  }),
  watch: {
    name(newName) {
      this.text = newName;
    },
  },
  methods: {
    addnewTodo(e) {
      if (e.keyCode === 13) {
        this.temp.title = this.text;
        this.items.push(this.temp);
        // console.log(this.items)
        this.text = "";
      }
    },
    edit(obj) {
      console.log("Edit Button clicked");
      this.text=obj;
    },
  },
};
</script>
