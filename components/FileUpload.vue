<template>
  <form v-on:submit.prevent @change="handleFilesUpload()" enctype="multipart/form-data" id="take-picture-form">
    <Button plain>
      {{ $t('button.scan') }}
      <input accept="image/*" type="file" id="files" name="file" ref="file"/>
    </Button>
  </form>
</template>

<script>
import Button from './Button'

export default {
  components: {
    Button
  },
  data () {
    return {
      file: ''
    }
  },
  methods: {
    handleFilesUpload () {
      this.file = this.$refs.file

      this.$axios({
        url: 'https://1bd20287.ngrok.io/dextra',
        method: 'post',
        // here was empty...only onsubmit() has file in that input
        // so onchange() file could trigger onsubmit() of form but you cannot onchange/ file send empty request
        data: new FormData(window.$('#take-picture-form')[0]),
        config: {
          headers: {
            'Content-Type': 'multipart/form-data'
          }
        }
      }).then(e => {
        console.log('SUCCESS!!', e)
      })
        .catch(e => {
          console.log('FAILURE!!', e.message)
          // Here can be also that you submited picture of an animal
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
