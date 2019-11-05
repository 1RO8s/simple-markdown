<template>
  <v-app>
    <v-app-bar app>
      <v-toolbar-title class="headline">
        <span>Markdown</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn
        text
        href="https://github.com/vuetifyjs/vuetify/releases/latest"
        target="_blank"
      >
        <span class="mr-2">Latest Release</span>
      </v-btn>
    </v-app-bar>
    <v-content>
      <Top/>
    </v-content>
  </v-app>
</template>

<script>
//import HelloWorld from './components/HelloWorld';
import Top from './components/Top';

export default {
  name: 'App',
  components: {
    Top
  },
  data: () => ({
    //
  }),
};
</script>
