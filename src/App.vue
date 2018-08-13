<template>
  <div id="app" class="text-center">
    <h1>Translator</h1>
    <h5>Powered By Vue.js</h5>
    <br>
    <TranslateForm v-on:formSubmit='translateText'></TranslateForm>
    <br>
    <TranslateOutput v-text="translatedText"></TranslateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'app',
  components:{
    TranslateForm,
    TranslateOutput
  },
  data: function(){
    return {
      translatedText:''
    }
  },
  methods: {
    translateText:function(text, language){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180809T055032Z.08259cb69f50e1f9.141cdf57306969b452276af3adb943302804f1d8&lang='+language+'&text='+text)
      .then((response) => {
        this.translatedText = response.body.text[0];
      });
    }
  }
}
</script>

<style>
body {
  background:#fefefe;
}
</style>
