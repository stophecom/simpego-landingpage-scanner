<template>
  <form v-on:submit.prevent @change="handleFilesUpload()" enctype="multipart/form-data" id="take-picture-form">
    <Button plain>
      {{ $t('button.upload') }}
      <input accept="image/*" type="file" id="files" name="file" ref="file"/>
    </Button>
  </form>
</template>

<script>
/* eslint-disable */
import Button from './Button'

export default {
  components: {
    Button
  },
  data () {
    return {
      file: '',
      data: {},
      error: false
    }
  },
  methods: {
    handleFilesUpload () {
      this.$axios({
        url: 'https://1bd20287.ngrok.io/dextra',
        method: 'post',
        data: new FormData(document.getElementById('take-picture-form')),
        config: {
          headers: {
            'Content-Type': 'multipart/form-data'
          }
        }
      }).then(({data}) => {
        this.data = data.response
        this.$emit('success', data)
        // console.log('SUCCESS!!', data)
      })
        .catch(e => {
          console.warn('FAILURE!!', e.message)
          this.error = true
        })
    }
  }
}
</script>

<style lang="scss">

input[type=file] {
  position: absolute;
  top: 0;
  right: 0;
  left: 0;
  bottom: 0;
  width: 100%;
  margin: 0;
  padding: 0;
  font-size: 20px;
  cursor: pointer;
  opacity: 0;
}
</style>
