<template lang="pug">
  .v-container.pa-4
    // Main content
    v-layout(column
    justify-center
    align-center).text-center
      v-flex(v-if='!$route.hash' xs12 md10)
        .headline.pb-4 Hi, enter HTML below and click "generate". You will be redirected to the url that contains this html and renders it. Share that url with anyone!
        v-text-field(label="HTML" placeholder="HTML" v-model="html")
        v-btn(@click='submit') Generate
        br
        br
        a(href='https://github.com/backmeupplz/generate-websites') Fully open source
      div(v-else v-html='_unescape($route.hash.substr(1))')
</template>

<script lang="ts">
import Vue from "vue";
import Component from "vue-class-component";

@Component
export default class Home extends Vue {
  html = "";

  submit() {
    window.location.href = `https://backmeupplz.github.io/generate-websites/#${this.html}`;
  }

  _unescape(str: string) {
    return unescape(str);
  }
}
</script>
