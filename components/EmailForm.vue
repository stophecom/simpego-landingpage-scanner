<template>
  <form
    class="form"
    @change="checkForm"
    @submit.prevent="onSubmit"
    novalidate="true"
  >
    <label class="form__label" for="email">{{ $t('label') }}</label>
    <div class="form__input">
      <input class="input" type="email" id="email" v-model="email" :placeholder="$t('placeholder')">
      <ul class="form__error" v-if="errors.length">
        <li v-for="(error, key) in errors" :key="key">{{ error }}</li>
      </ul>
      <Button :disabled="(!!errors.length || !email)">
        Submit
      </Button>
    </div>
    </form>
</template>

<script>
import Button from './Button'

export default {
  components: {
    Button
  },
  data: () => ({
    email: '',
    errors: [],
    formSuccess: false
  }),
  props: {
    carDetails: {
      type: Object,
      default: {}
    }
  },
  methods: {
    checkForm: function (e) {
      this.errors = []

      if (!this.email) {
        this.errors.push(this.$t('errorRequired'))
      } else if (!this.validEmail(this.email)) {
        this.errors.push(this.$t('errorInvalid'))
      }

      if (!this.errors.length) {
        return true
      }

      e.preventDefault()
    },
    validEmail: function (email) {
      var re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
      return re.test(email)
    },
    onSubmit: function () {
      var self = this
      window.$.ajax({
        url: 'https://jumprock.co/mail/simpego',
        method: 'POST',
        data: {
          subject: 'New car insurance lead',
          email: self.email,
          message: JSON.stringify(self.carDetails)
        },
        dataType: 'json'
      }).then(function () {
        self.$emit('success', true)
      }).catch(function () {
        self.$emit('failure', true)
      })
    }
  },
  i18n: {
    messages: {
      en: {
        label: 'Email',
        placeholder: 'Your e-mail address',
        errorRequired: 'Email required.',
        errorInvalid: 'Valid email required.'

      },
      de: {
        label: 'E-Mail',
        placeholder: 'Deine E-Mail-Adresse',
        errorRequired: 'E-mail-Adresse fehlt.',
        errorInvalid: 'E-Mail-Adresse ungültig.'
      }
    }
  }
}
</script>
