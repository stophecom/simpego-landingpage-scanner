<template>
  <Section class="scanner">

    <div v-if="carBrandAndType">
      <div class="status status--success">{{ $t('statusSuccess') }}</div>
      <h1>{{ carBrandAndType }}</h1>
      <p class="section__headline">{{ $t('successMessage') }}</p>
      <div class="box">
        <template v-if="emailSuccess">
          <p class="box__intro box__intro--success">{{ $t('postEmailSuccess') }}</p>
        </template>
        <template v-else-if="emailFailure">
          <p class="box__intro box__intro--error">{{ $t('postEmailFailure') }}</p>
        </template>
        <template v-else>
          <p class="box__intro">{{ $t('postEmail') }}</p>
          <EmailForm :carDetails="carDetails" @success="emailSuccess = true" @failure="emailFailure = true" />
        </template>
      </div>
    </div>
    <div v-else>
      <h1>{{ $t('title') }}</h1>
      <div class="section__headline">{{ $t('headline') }}</div>
      <ul class="manual">
        <li>
          <img alt="Scanner" src="/images/scan.svg" />
          <div class="description"><strong>1.</strong> {{ $t('manual1') }}</div>
        </li>
        <li>
          <img alt="Done" src="/images/done.svg" />
          <div class="description"><strong>2. Boom.</strong> {{ $t('manual2') }}</div>
        </li>
      </ul>
      <div class="section__cta">
        <FileUpload v-on:success="handleData"/>
      </div>
    </div>
  </Section>
</template>

<script>
import { get } from 'lodash'

import Button from '../components/Button'
import EmailForm from '../components/EmailForm'
import FileUpload from '../components/FileUpload'
import Section from '../components/Section'

export default {
  components: {
    Button,
    EmailForm,
    FileUpload,
    Section
  },
  data: () => ({
    carBrandAndType: '',
    carDetails: {},
    emailSuccess: false,
    emailFailure: false
  }),
  methods: {
    handleData (data) {
      this.carBrandAndType = get(data, '[0].fields.brandAndType')
      this.carDetails = get(data, '[0].fields')
    }
  },
  i18n: {
    messages: {
      en: {
        title: 'Be a winner',
        headline: 'Test our scanner and win car insurance for the whole year. A photo of your vehicle registration document is enough. Here\'s how it works:',
        manual1: 'Take a picture of your vehicle registration document',
        manual2: 'Done. You take part in the lottery!',
        successMessage: 'Wow, what a nice car. Let\'s get that baby insured right away!',
        statusSuccess: 'Vehicle recognition successful:',
        postEmail: 'Please leave your email and receive your quote in no time',
        postEmailSuccess: 'Huge success. You are about to save a substantial amount of money. We\'ll get back at you with your personal offer shortly.',
        postEmailFailure: 'An error occured. Bitte contact support via E-Mail: hallo@simpego.ch'
      },
      de: {
        title: 'Mitmachen und Gewinnen',
        headline: 'Teste unseren Scanner und gewinne eine Jahresversicherung für dein Auto. Ein Foto von deinem Fahrzeugausweis genügt. So funktionierts:',
        manual1: 'Fahrzeugausweis fotografieren',
        manual2: 'Du nimmst am Gewinnspiel teil!',
        successMessage: 'Wow, was für ein tolles Auto. Lass uns das gleich versichern!',
        statusSuccess: 'Fahrzeugerkennung erfolgreich:',
        postEmail: 'Hinterlasse deine E-mail und wir melden uns umgehend mit dem besten Angebot.',
        postEmailSuccess: 'Bravo - so einfach geht sparen. Wir melden uns in Kürze mit deinem persönlichen Angebot!',
        postEmailFailure: 'Es ist ein Fehler aufgetreten. Bitte kontaktiere uns via E-Mail: hallo@simpego.ch'
      }
    }
  }
}
</script>

<style lang="scss">
.status {
  text-align: center;
  font-size: 0.8rem;
  text-transform: uppercase;
  margin-bottom: 2em;

  &--error {
    color: $error;
  }

  &--success {
    color: $primary;
  }
}

.box {
  align-items: center;
  border: 1px solid $colorBorderStrong;
  border-radius: $borderRadius;
  background-color: $defaultBackground;
  display: flex;
  flex-direction: column;
  justify-content: center;
  margin: 1rem auto;
  padding: 2rem 1rem;

   @media screen and (min-width: $breakpointSmall) {
    max-width: 460px;
    padding: 2rem;
  }

  &__intro {
    text-align: center;

    &--success {
      color: $primary;
    }

    &--error {
      color: $error;
    }

    &:not(:last-child) {
      margin-bottom: 2rem;
    }
  }
}

.manual {
  align-items: center;
  display: flex;
  flex-direction: column;
  justify-content: center;
  margin: 0;
  padding: 0;
  text-align: center;

  @media screen and (min-width: $breakpointMini) {
    align-items: flex-start;
    flex-direction: row;
  }

  li {
    padding: 1.5rem;
    max-width: 250px;
  }
}
</style>
