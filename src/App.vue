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
            <v-app-bar-nav-icon> </v-app-bar-nav-icon>
            <v-app-bar-title>Welcome to Chris App!</v-app-bar-title>
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


<style lang="scss" scoped>
:root {
  --popper-theme-background-color: #333333;
  --popper-theme-background-color-hover: #333333;
  --popper-theme-text-color: #ffffff;
  --popper-theme-border-width: 0px;
  --popper-theme-border-style: solid;
  --popper-theme-border-radius: 5px;
  --popper-theme-padding: 10px;
  --popper-theme-box-shadow: 0 6px 30px -6px rgba(0, 0, 0, 0.25);
}
</style>