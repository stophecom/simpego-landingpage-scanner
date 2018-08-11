<template>
  <Button plain>
    {{ $t('button.scan') }}
    <input accept="image/*" type="file" id="files" ref="file" @change="handleFilesUpload()"/>
  </Button>
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
      this.file = this.$refs.file.files[0]

      this.$axios.post('https://1bd20287.ngrok.io/dextra',
        this.file,
        {
          headers: {
            'Content-Type': 'multipart/form-data'
          }
        }
      ).then(() => {
        console.log('SUCCESS!!')
      })
      .catch(() => {
        console.log('FAILURE!!')
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
