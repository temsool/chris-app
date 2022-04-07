<template>
  <v-app>
    <v-main id="main-app">
      <v-card
        max-width="900"
        class="mx-auto"
        style="border-radius: 0 !important"
        color="grey-lighten-4"
      >
        <v-layout>
          <v-app-bar color="red-darken-4" class="text-white">
            <v-app-bar-title> </v-app-bar-title>
          </v-app-bar>

          <v-main id="main-cointainer">
            <v-container fluid>
              <router-view />
            </v-container>
          </v-main>
        </v-layout>
      </v-card>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "App",

  data: () => ({
    //
  }),
};
</script>
