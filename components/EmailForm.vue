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
        url: 'https://jumprock.co/mail/santihans',
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

<style lang="scss">
.form {
  width: 100%;

  &__label {
    margin-left: 0.2rem;
    margin-bottom: 0.5rem;
    color: $text;
    font-size: 0.6rem;
    font-weight: 600;
    line-height: 1.1;
    text-transform: uppercase;
  }

  &__input {
    display: flex;
    position: relative;
  }

  &__error {
    color: $error;
    font-size: 0.6rem;
    font-weight: 600;
    line-height: 1.1;
    margin-left: 0.2rem;
    position: absolute;
    top: calc(100% + 0.2rem);
    text-transform: uppercase;
  }

  .input {
    appearance: none;
    box-shadow: none;
    border-radius: $borderRadius;
    border: 1px solid $colorBorder;
    display: flex;
    font-size: 1rem;
    height: 2.8rem;
    outline: 0;
    padding-left: 0.8em;
    padding-right: 0.6em;
    width: 100%;

    &:active,
    &:focus {
      border-color: $primary;
    }
  }
}
</style>
