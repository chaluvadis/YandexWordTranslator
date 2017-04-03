<template>
  <div class="text-center" id="app">
    <h1>Word Translator</h1>
    <h5>Powered by Vue.js</h5>
    <TranslateForm v-on:formSubmit="translateText"></TranslateForm>
    <TranslateOutput v-text="translatedText"></TranslateOutput>
    <FooterTemplate></FooterTemplate>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'
import FooterTemplate from './components/FooterTemplate'
export default {
  name: 'app',
  components: {
    TranslateForm,
    TranslateOutput,
    FooterTemplate
  },
  data: function(){
    return {
      translatedText:''
    }
  },
  methods: {
    translateText : function(text, language){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170331T181249Z.d19f956d16178eb8.779af0614287339c2a062194a4cf13aaf4527e98&lang=' + language +'&text='+text)
      .then((response)=>{
        this.translatedText = response.body.text[0];
      });
    }
  }
}
</script>

<style>
  body{
    background:#fefefe;
  }
</style>
