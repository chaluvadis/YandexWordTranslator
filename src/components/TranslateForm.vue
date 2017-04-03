<template>
  <div class="row" id="translateForm">
        <div class="col-md-6 col-md-offset-3">
            <form id="transForm" class="form-inline well" v-on:submit="formSubmit">
                <input class="form-control" style="margin-right:10px;" type="text" v-model="textToTranslate" placeholder="Enter text to translate">
                <select class="form-control" style="margin-right:10px;" v-model="language">
                    <option value="te">Telugu</option>
                    <option value="ta">Tamil</option>
                    <option value="hi">Hindi</option>
                    <option value="ru">Russian</option>
                    <option value="es">Spanish</option>
                    <option value="kn">Kannada</option>
                </select>
                <input class="btn btn-primary" type="submit" value="Translate">
            </form>
        </div>
  </div>
</template>

<script>
export default {
  name: 'translateForm',
  data(){
      return {
          textToTranslate:'',
          language: ''
      }
  },
  created(){
    this.language = 'te';
  },
  methods: {
      formSubmit(e){
          this.$emit('formSubmit', this.textToTranslate, this.language);
          e.preventDefault();
      }
  }
}
</script>

<style>
    #transForm {
        border-radius: 10px;
        border:1px #ccc solid;
    }
</style>
