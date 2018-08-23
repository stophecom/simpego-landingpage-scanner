<template>
  <div>
    <div v-if="loading">
      <Spinner />
    </div>
    <form v-else class="form" v-on:submit.prevent @change="handleFilesUpload()" enctype="multipart/form-data" id="take-picture-form">
      <Button plain>
        <span class="fa fa-camera"></span>
        {{ $t('button.upload') }}
        <input accept="image/*" type="file" id="files" name="file" ref="file"/>
      </Button>
      <div v-if="error" class="form__error">{{ $t('scanError') }}</div>
    </form>
  </div>
</template>

<script>
/* eslint-disable */
import Button from './Button'
import Spinner from './Spinner'

export default {
  components: {
    Button,
    Spinner
  },
  data () {
    return {
      file: '',
      data: {},
      error: false,
      loading: false
    }
  },
  methods: {
    handleFilesUpload () {
      this.loading = true
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
        this.loading = false
        this.data = data.response
        this.$emit('success', data)
      })
        .catch(e => {
          this.loading = false
          console.warn('FAILURE!!', e.message)
          this.error = true
        })
    }
  },
  i18n: {
    messages: {
      en: {
        scanError: 'Vehicle recognition failed. You posted some random picture, did you? :) Try with a real vehicle registration (Inside).'
      },
      en: {
        scanError: 'Fahrzeugerkennung fehlgeschlagen. Das Bild war kein Ausweis, stimmts? :) Versuche es mit einem richtigen Ausweis (Innenseite).'
      }
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
