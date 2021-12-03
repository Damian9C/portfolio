<template>
  <div class="bannerHome">
    <v-navigation-drawer v-model="isActive" temporary app right>
      <v-list-item class="mt-2">
        <div class="d-flex flex-column">
          <span class="app-logo-title">
            Damian Chavez<br/>
            <span class="Monserrat">
              Desarrollador web
            </span>
          </span>
        </div>
      </v-list-item>

      <v-list>
        <v-divider />

        <v-list-item v-for="(item, i) of menuLinks" :key="i" link @click="scrollToSection(item.route)">
          <v-list-item-content>
            <v-list-item-title class="app-font-size">
              {{ item.title }}
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar elevation="3" fixed class="app-bar-style " color="white" app>
      <div class="v-app-bar-title Montserrat-SemiBold">
        Damian Chavez<br/>
        <span class="Monserrat">
          Desarrollador web
        </span>
      </div>
      <v-spacer/>

      <div class="app-font-content d-none d-md-flex Montserrat-Bold">
        <v-btn
            v-for="(item, j) of menuLinks" :key="j"
            text
            small
            :ripple="false"
            color="grey"
            @click="scrollToSection(item.route)"
        >
          {{ item.title }}
        </v-btn>
      </div>

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

.v-app-bar-title{
  letter-spacing: .2mm;
}

.v-app-bar-title span{
  font-size: 14px;
}

.app-font-size {
  font-size: 14px;
}

.app-font-content{
  color: #3d3d3d;
}

</style>
