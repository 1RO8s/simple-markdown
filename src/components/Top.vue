<template>
  <v-container fluid>
    <v-row>
      <v-col>
          <v-textarea label="TEXTAREA" v-model="markdown" color="purple lighten-4" outlined auto-grow></v-textarea>
      </v-col>
      <v-col>
        <v-card class="preview" v-html="preview()" outlined>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import marked from "marked";
export default {
  props:{
    md:{
      type: String,
      required: true
    }
  },
  data: () => ({
    markdown:this.md,
    //notes:notes
  }),
  methods: {
    preview: function(){
      return marked(this.markdown);
    },
    save: function(){
      localStorage.simpleMarkdown = JSON.stringify({
        notes:this.notes
      });
    }
  }
};
</script>
