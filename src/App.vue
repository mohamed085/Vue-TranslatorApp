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
    translateText(text) {
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170329T180255Z.3c18d2dc7b65d525.f23ed9a9efa992bded4ef96334e3c154f61d2dea&lang=ar&text='+text)
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
