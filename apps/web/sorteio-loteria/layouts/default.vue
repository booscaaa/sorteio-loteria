<template>
  <v-app dark>
    <v-app-bar app>
      <v-spacer />
      <v-img max-height="28" max-width="28" src="logo-mega-sena.png"></v-img>
      <v-toolbar-title class="px-2 title" v-text="title" />
      <v-img max-height="28" max-width="28" src="logo-mega-sena.png"></v-img>
      <v-spacer />
    </v-app-bar>
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
    <v-footer app class="d-flex justify-center">
      UsGuri
      <span class="pl-2">&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: "DefaultLayout",
  data() {
    return {
      title: "MEGA SENA DUS GURI",
    };
  },
};
</script>

<style lang="scss" scoped>
.v-toolbar__title {
  font-size: 2rem !important;
}
.title {
  font-style: normal;
  font-weight: 800;
  line-height: 32px;
  color: #21986A;
}
</style>
