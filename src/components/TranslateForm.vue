<template>
  <div id="translateform">
    <form id="transForm" v-on:submit="formSubmit">
        <input class="form-control" width="50px" type="text" v-model="textToTranslate" placeholder="请输入内容">
        <br>
        <select class="form-control" v-model="language">
          <option value="zh">中文</option>
          <option value="ja">日文</option>
          <option value="en">英文</option>
        </select>
        <br>
        <input class="btn btn-default" type="submit" value="翻译">
    </form>
  </div>
</template>

<script>
export default {
  name: 'translateForm',
  data(){
    return {
      textToTranslate:'',
      language:''
    }
  },
  created() {
    this.language = 'zh';
  },
  methods: {
    formSubmit(e){
      this.$emit('formSubmit', this.textToTranslate, this.language);
      e.preventDefault()
    }
  }
}
</script>

<style>
  #transForm {
  width: 14%;
  position: relative;
  left: 43%;
  }
  .btn {
    width: 100%;
  }
</style>
