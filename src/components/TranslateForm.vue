<template>
  <div class="row" id="translateForm">
    <div class="col-md-6 col-md-offset-3">
      <form id="transForm" class="form-inline well" v-on:submit="formSubmit">
        <input class="form-control" type="text" v-model="textToTranslate" placeholder="Enter a Word...">
        <select class="form-control" v-model="language">
          <option value="ar">Arabic</option>
          <option value="es">Spanish</option>
          <option value="fr">French</option>
          <option value="zh">Chinese</option>
        </select>
        <input class="btn btn-primary" type="submit" value="Translate">
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "TranslateForm",
  data() {
    return {
      textToTranslate: '',
      language:''
    }
  },
  created() {
    this.language = 'ar';
  },
  methods: {
    formSubmit(e) {
      this.$emit('formSubmit', this.textToTranslate)
      e.preventDefault()
    }
  }
}
</script>

<style scoped>

</style>