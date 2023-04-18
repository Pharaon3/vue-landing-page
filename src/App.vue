<template>
  <v-app>
    <navigation :color="color" :flat="flat" />
    <v-main class="pt-0">
      <home />
      <v-container fluid>
        <v-row align="center" justify="center">
          <v-col cols="10">
            <v-row align="center" justify="center">
              <v-col cols="12" md="3">
                <about />
              </v-col>
              <v-col cols="12" md="5">
                <download />
              </v-col>
              <v-col cols="12" md="4">
                <pricing />
              </v-col>
            </v-row>
          </v-col>
        </v-row>
      </v-container>
      <contact />
    </v-main>
    <v-scale-transition>
      <v-btn fab v-show="fab" v-scroll="onScroll" dark fixed bottom right color="secondary" @click="toTop">
        <v-icon>mdi-arrow-up</v-icon>
      </v-btn>
    </v-scale-transition>
    <foote />
  </v-app>
</template>

<style scoped>
.v-main {
  background-image: url("~@/assets/img/bgMain.png");
  background-attachment: fixed;
  background-position: center;
  background-size: cover;
}
</style>

<script>
import navigation from "./components/Navigation";
import foote from "./components/Footer";
import home from "./components/HomeSection";
import about from "./components/AboutSection";
import download from "./components/DownloadSection";
import pricing from "./components/PricingSection";
import contact from "./components/ContactSection";

export default {
  name: "App",

  components: {
    navigation,
    foote,
    home,
    about,
    download,
    pricing,
    contact,
  },

  data: () => ({
    fab: null,
    color: "",
    flat: null,
  }),

  created() {
    const top = window.pageYOffset || 0;
    if (top <= 60) {
      this.color = "white";
      this.flat = true;
    }
  },

  watch: {
    fab(value) {
      if (value) {
        this.color = "white";
        this.flat = false;
      } else {
        this.color = "white";
        this.flat = true;
      }
    },
  },

  methods: {
    onScroll(e) {
      if (typeof window === "undefined") return;
      const top = window.pageYOffset || e.target.scrollTop || 0;
      this.fab = top > 60;
    },
    toTop() {
      this.$vuetify.goTo(0);
    },
  },
};
</script>
