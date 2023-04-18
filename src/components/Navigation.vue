<template>
  <div>
    <v-navigation-drawer v-model="drawer" app temporary dark src="@/assets/img/bgDrawer.jpg">
      <v-list>
        <v-list-item>
          <v-list-item-avatar>
            <img src="@/assets/img/logo.webp" alt="Logo" />
          </v-list-item-avatar>
          <v-list-item-content>
            <v-list-item-title class="title">Restaurant</v-list-item-title>
            <v-list-item-subtitle>Jannat</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </v-list>

      <v-divider />

      <v-list dense>
        <v-list-item v-for="([icon, text, link], i) in items" :key="i" link @click="$vuetify.goTo(link)">
          <v-list-item-icon class="justify-center">
            <v-icon>{{ icon }}</v-icon>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title class="subtitile-1">{{
              text
            }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar app :color="color" :flat="flat" class="px-15" :class="{ expand: flat }">
      <v-toolbar-title>
        <v-img src="@/assets/img/logo.webp" max-width="50px" />
      </v-toolbar-title>
      <v-spacer />
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" class="mr-4" v-if="isXs" />
      <div v-else>
        <v-btn text @click="$vuetify.goTo('#hero')">
          <span class="mr-2 iBWChl">Home</span>
        </v-btn>
        <v-btn text @click="$vuetify.goTo('#features')">
          <span class="mr-2 iBWChl">Menu</span>
        </v-btn>
        <v-btn text @click="$vuetify.goTo('#download')">
          <span class="mr-2 iBWChl">Reservation</span>
        </v-btn>
        <v-btn text @click="$vuetify.goTo('#pricing')">
          <span class="mr-2 iBWChl">Gallery</span>
        </v-btn>
        <v-btn text @click="$vuetify.goTo('#pricing')">
          <span class="mr-2 iBWChl">Contact</span>
        </v-btn>
        <v-btn rounded outlined text @click="$vuetify.goTo('#contact')">
          <span class="mr-2 iBWChl"><v-img src="@/assets/img/flag-united-kingdom.svg" max-width="50px" /></span>
        </v-btn>
      </div>
    </v-app-bar>
  </div>
</template>

<style scoped>
.v-toolbar {
  transition: 0.6s;
}

.expand {
  height: 80px !important;
  padding-top: 10px;
}
.iBWChl {
  font-size: 17px;
  padding: 0px;
  margin: 0px;
  font-weight: 700;
  text-align: center;
}
</style>

<script>
export default {
  data: () => ({
    drawer: null,
    isXs: false,
    items: [
      ["mdi-home-outline", "Home", "#hero"],
      ["mdi-information-outline", "Menu", "#features"],
      ["mdi-download-box-outline", "Reservation", "#download"],
      ["mdi-currency-usd", "Gallery", "#pricing"],
      ["mdi-email-outline", "Contact", "#contact"],
    ],
  }),
  props: {
    color: String,
    flat: Boolean,
  },
  methods: {
    onResize() {
      this.isXs = window.innerWidth < 850;
    },
  },

  watch: {
    isXs(value) {
      if (!value) {
        if (this.drawer) {
          this.drawer = false;
        }
      }
    },
  },
  mounted() {
    this.onResize();
    window.addEventListener("resize", this.onResize, { passive: true });
  },
};
</script>
