<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
          transition="scale-transition"
          width="40"
        />

        <h1>Ag Grid Test</h1>
      </div>

      <v-spacer></v-spacer>

      <v-btn
        href="https://github.com/vuetifyjs/vuetify/releases/latest"
        target="_blank"
        text
      >
        <span class="mr-2">Latest Release</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
        <v-tabs
          v-model="tab"
          align-with-title
        >
          <v-tabs-slider color="yellow"></v-tabs-slider>

          <v-tab
            v-for="item in items"
            :key="item.text"
          >
            {{ item.text }}
          </v-tab>
        </v-tabs>
        <v-tabs-items v-model="tab">
          <v-tab-item
            v-for="item in items"
            :key="item.text"
          >
          <keep-alive>
            <component :is="item.comp"></component>
          </keep-alive>
          </v-tab-item>
        </v-tabs-items>
      
    </v-main>
  </v-app>
</template>

<script>
import Basic from './components/Basic';
import HelloWorld from './components/HelloWorld';

export default {
  name: 'App',

  components: {
    HelloWorld,
    Basic
  },

  data: () => ({
      tab: null,
      items: [
        { text:'basic', comp:"Basic" },
        { text:'second', comp:"HelloWorld" },
      ],
  }),
};
</script>

<style lang="scss">
   @import "~ag-grid-community/dist/styles/ag-grid.css";
   @import "~ag-grid-community/dist/styles/ag-theme-alpine.css";
</style>