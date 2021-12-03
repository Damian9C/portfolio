<template>
  <v-app>
    <v-main>
      <nav-bar/>
      <router-view/>
    </v-main>
  </v-app>
</template>

<script>

import NavBar from "./layouts/navBar";
export default {
  name: 'App',
  components: {NavBar},
  data: () => ({
    //
  }),
};
</script>
