<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5>简单 / 易用 / 便捷 / </h5>
    <translateForm v-on:FormSumbit="translateText"></translateForm>
    <trans v-text:FormSumbit="translatedText"></trans>
  </div>
</template>

<script>
import translateForm from './components/translateForm'
import trans from './components/trans'

export default {
  name: 'App',
  data(){
      return {
        translatedText:''
      }
  },
  components: {
    translateForm,trans,
  },
  methods:{
    translateText:function (text,language) {
        this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180424T151710Z.ced018bd6d621af1.' +
          'cb4b9a405e083f2334868a3fb3484fddc91ff1c6&lang='+language+'&text='+text)
          .then(function (response) {
              console.log(response)
            this.translatedText = response.body.text[0]
          })
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
