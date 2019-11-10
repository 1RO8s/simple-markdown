<template>
  <v-app>
    <v-app-bar color="primary" clipped-left dark app>
      <v-app-bar-nav-icon></v-app-bar-nav-icon>
      <v-toolbar-title>Simple Markdown</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn v-on:click="save()">Save</v-btn>
    </v-app-bar>
    <v-navigation-drawer clipped app>
      <v-list>
        <v-list-item v-for="title in titles()" :key="title">
          <v-list-item-content>
            <v-list-item-title>{{title}}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-content app>
      <v-container fluid>
        <v-row no-gutters>
          <v-text-field></v-text-field>
        </v-row>
        <v-row no-gutters>
          <v-col>
            <v-sheet min-height="200" tile>
              <v-textarea label="TEXTAREA" v-model="markdown" color="purple lighten-4" solo flat auto-grow :messages="notes[1]"/>
            </v-sheet>
          </v-col>
          <v-col>
            <v-card class="preview" v-html="preview()" outlined tile>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-content>
    <v-footer color="primary" dark app>
      Vuetify
    </v-footer>
  </v-app>
</template>

<script>
//import HelloWorld from './components/HelloWorld';
//import Top from './components/Top';
import marked from "marked";

var simpleMarkdown = JSON.parse(localStorage.simpleMarkdown);
var notes = simpleMarkdown.notes;

export default {
  name: 'App',
  components: {
    //Top
  },
  data: () => ({
    items: [
      { title: 'Dashboard', icon: 'dashboard' },
      { title: 'Account', icon: 'account_box' },
      { title: 'Admin', icon: 'gavel' },
    ],
    notes:notes,
    markdown:notes[0]
  }),
  methods:{
    titles(){
      return this.notes.map(e=>e.split(/\r\n|\n|\r/)[0]);
    },
    preview: function(){
      return marked(this.markdown);
    },
    save: function(){
      this.notes[0] = this.markdown;
      console.log("save!!");
      console.log(this.notes);
      localStorage.simpleMarkdown = JSON.stringify({
        notes:this.notes
      });
    }
  }
};
</script>
<style lang="scss">
.v-text-field__details {
  display: none;
}
</style>
