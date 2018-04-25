<template>
  <div id="translateForm" class="row">
    <div class="col-md-6 col-md-offset-3">
      <form  class="well form-inline" v-on:submit="translateSumbit">
        <input class="form-control" type="text" placeholder="请输入你要翻译的内容" v-model="translateText">
        <select v-model="language" class="form-control">
          <option value="en">英语</option>
          <option value="ru">俄罗斯语</option>
          <option value="ko">韩语</option>
          <option value="ja">日语</option>
        </select>
        <input type="submit" class="btn btn-primary" value="翻译">
      </form>
    </div>
  </div>
</template>

<script>
  export default ({
    name:'translateForm',
    data(){

      return {
        translateText:'',
        language:''
      }
    },
    methods:{
      translateSumbit:function (e) {
        //alert(this.translateText);
        this.$emit('FormSumbit',this.translateText,this.language)
        e.preventDefault();
      }
    },
    created:function () {
      this.language = 'en'
    }
  })
</script>
