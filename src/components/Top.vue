<template>
  <v-container>
    <v-row>
      <v-col>

          <v-textarea label="TEXTAREA" v-model="markdown" color="deep-purple" outlined auto-grow></v-textarea>

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

let initTxt = `
# Title
## Subtitle
### Section
#### point
`;

export default {
  data: () => ({
    markdown:initTxt
  }),
  methods: {
    preview: function(){
      return marked(this.markdown);
    }
  }
};
</script>
