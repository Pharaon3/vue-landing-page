<template>
  <section id="hierarchy">
    <v-container fluid>
      <v-row align="center" justify="center">
        <v-col cols="10">
          <v-text-field v-model="search" append-icon="mdi-magnify" label="Search" single-line hide-details
            @keyup.enter="searchItems"></v-text-field>
            <v-list-item v-for="([text, link], i) in groups" :key="i" link @click="$vuetify.goTo(link)">
              <v-list-item-content>
                <v-list-item-title class="subtitile-1">{{
                  text
                }}</v-list-item-title>
              </v-list-item-content>
            </v-list-item>
        </v-col>
      </v-row>
    </v-container>
  </section>
</template>

<style scoped>
#about {
  background-color: #f4f7f5;
}
</style>

<script>
export default {
  data() {
    return {
      search: '',
      groups: [
        ["Lunch Dishes", "#Lunch"],
        ["Warme vorspeisen", "#Warme"],
        ["Suppen", "#Suppen"],
        ["Salate", "#Salate"],
        ["Beilagen", "#Beilagen"],
        ["Spezialitäten aus dem tandoor", "#tandoor"],
        ["Vegetarische-spezialitäten", "#Vegetarische"],
        ["Huhn-spezialitäten", "#Huhn"],
        ["Enten-spezialitäten", "#Enten"],
        ["Lamm-spezialitäten", "#Lamm"],
        ["Fisch-spezialitäten", "#Fisch"],
      ],
    };
  },
  methods: {
    searchItems() {
      // Do something with the search query
      console.log('Search query:', this.search);
    },
  },
};
</script>