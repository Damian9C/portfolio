<template>
  <div class="bannerHome">
    <v-navigation-drawer v-model="isActive" temporary app right>
      <v-list-item class="mt-2">
        <div class="d-flex flex-column">
          <span class="app-logo-title">
            Damian Chavez<br/>
            <span class="v-app-bar-subTitle Monserrat">
              Desarrollador web
            </span>
          </span>
        </div>
      </v-list-item>

      <v-list>
        <v-divider />

        <v-list-item
            v-for="(item, i) of menuLinks"
            :key="i"
            link
            color="#3d3d3d"
            @click="scrollToSection(item.route)"
            class="Montserrat-Medium"
        >
          <v-list-item-content>
            <v-list-item-title class="app-font-size">
              {{ item.title }}
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
        elevation="0"
        fixed
        class="app-bar-style "
        dense
        color="white"
        app
    >
      <v-spacer/>
      <div
          class="app-font-content d-none d-md-flex Montserrat-Bold"
          v-for="(item, j) of menuLinks" :key="j"
      >
        <v-spacer/>
        <v-btn
            text
            small
            :ripple="false"
            color="#3d3d3d"
            @click="scrollToSection(item.route)"
        >
          {{ item.title }}
        </v-btn>
      </div>
      <v-spacer/>

      <div class="d-flex d-md-none">
        <v-btn icon @click="openDrawer">
          <v-icon>
            mdi-menu
          </v-icon>
        </v-btn>
      </div>
    </v-app-bar>
  </div>
</template>

<script>
export default {
  name: "navBar",
  data: () => ({
    isActive: null,
    menuLinks: [
      {
        title: 'Inicio',
        route: 'mainBanner',
      },
      {
        title: 'Acerca de',
        route: 'aboutUs',
      },
      {
        title: 'Proyectos',
        route: 'career',
      },
      {
        title: 'Contacto',
        route: 'contact'
      }
    ]
  }),
  methods: {
    openDrawer() {
      this.isActive = true;
    },
    scrollToSection(elementName) {
      window.scrollTo({
        top: document.getElementById(elementName).offsetTop,
        behavior: 'smooth'
      });
      this.isActive = false;
    }
  }
}
</script>

<style scoped>

.app-logo-title{
  font-size: 18px;
  letter-spacing: .7mm;
  color: #3d3d3d;
}

.v-app-bar-subTitle{
  letter-spacing: .4mm;
  font-size: 12px;
}

.app-font-size {
  font-size: 14px;
}

.app-font-content{
  color: #3d3d3d;
}

</style>
