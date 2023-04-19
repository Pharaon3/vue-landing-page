<template>
  <section id="dishes">
    <v-container fluid>
      <v-row align="center" justify="center">
        <v-col cols="10">
          <v-row align="center" justify="center">
            <v-col cols="12" sm="8" class="black--text text-left">
              <h1 class="font-weight-strong mb-2 bg-darkyellow text-lg">Lunch dishes</h1>
              <h1 class="font-weight-light">
                Lunch dishes not available for delivery. Pickup possible
              </h1>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-container>
  </section>
</template>

<style scoped>
#dishes {
  height: 500px;
}
.bg-darkyellow{
  background-color: #fefce8;
}
#dishes .container,
#dishes .row {
  height: 100%;
}
</style>