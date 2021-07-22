<template>
  <div class="row" id="translateForm">
    <div class="col-md-6 col-md-offset-3">
      <form id="transForm" class="form-inline well" v-on:submit="formSubmit">
        <input class="form-control" type="text" v-model="textToTranslate" placeholder="Enter a Word...">
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
      textToTranslate: ''
    }
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