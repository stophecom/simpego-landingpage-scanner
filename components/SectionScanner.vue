<template>
  <Section class="scanner">
    <h1>{{ $t('title') }}</h1>
    <div class="section__headline">{{ $t('headline') }}</div>
    <ul class="manual">
      <li>
        <img alt="Scanner" src="/images/scan.svg" />
        <div class="description"><strong>1.</strong> {{ $t('manual1') }}</div>
      </li>
      <li>
        <img alt="Done" src="/images/done.svg" />
        <div class="description"><strong><del>2.</del> Boom.</strong> {{ $t('manual2') }}</div>
      </li>
    </ul>
    <div class="section__cta">
      <Button color="primary">{{ $t('button.scan') }}</Button>
      <Button color="transparent">{{ $t('button.upload') }}</Button>
    </div>
  </Section>
</template>

<script>
import Button from '../components/Button'
import Section from '../components/Section'

export default {
  components: {
    Button,
    Section
  },
  i18n: {
    messages: {
      en: {
        title: 'Save CHF 500 a year with one photo.',
        headline: 'Find the best car insurance in the entire Swiss market. A photo of your vehicle registration document is enough. Here\'s how it works:',
        manual1: 'Take a photo of your vehicle registration document',
        manual2: 'Simpego finds you the best deal.'

      },
      de: {
        title: 'Spare CHF 500  pro Jahr mit einem Foto.',
        headline: 'Finde die beste Autoversicherung auf dem gesamten Schweizer Markt. Ein Foto von deinem Fahrzeugausweis genügt. So funktionierts:',
        manual1: 'Fahrzeugausweis fotografieren',
        manual2: 'Simpege liefert dir das beste Angebot.'
      }
    }
  }
}
</script>

<style lang="scss">
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

    img {
    }
  }
}
</style>
