<template>
  <div class="text-center" id="app">
    <h1>Word Translator</h1>
    <h5 class="text-muted">Powered By Vue.js</h5>
    <hr>
    <TranslateForm v-on:formSubmit="translateText"></TranslateForm>
    <TranslateOutput v-text="translateWord"></TranslateOutput>
  </div>
</template>

<script>
import TranslateForm from "@/components/TranslateForm";
import TranslateOutput from "@/components/TranslateOutput";
export default {
  name: 'app',
  components: {
    TranslateOutput,
    TranslateForm
  },
  data() {
    return {
      translateWord: ''
      }
  },
  methods: {
    translateText(text, language) {
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/getLangs?key=&lang='+language+'&text='+text)
      .then(res => {
        this.translateText = res.body.text[0];
      })
    }
  }
}
</script>



<style>
body {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background:#fefefe;
}

</style>
