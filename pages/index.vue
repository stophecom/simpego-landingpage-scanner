<template>
<div class="index">
  <Hero backgroundImage="/images/background-car-3.jpg">
    <h1>{{ $t('hero.title') }}</h1>
    <p>{{ $t('hero.teaser') }}</p>
    <Button color="primary">{{ $t('button.calculateNow') }}</Button>
  </Hero>
  <SectionScanner />
  <Section alternative>
    <h2>{{ $t('why.title') }}</h2>
    <div class="section__headline">{{ $t('why.teaser') }}</div>
    <PartnerLogos/>
    <div class="section__cta">
      <Button color="secondary">{{ $t('button.learnMore') }}</Button>
    </div>
  </Section>
  </div>
</template>

<script>
import Button from '../components/Button'
import Hero from '../components/Hero'
import Section from '../components/Section'
import PartnerLogos from '../components/PartnerLogos'
import SectionScanner from '../components/SectionScanner'

export default {
  components: {
    Button,
    Hero,
    Section,
    PartnerLogos,
    SectionScanner
  },
  i18n: {
    messages: {
      en: {
        hero: {
          title: 'Car insurance drives you crazy? We fix that.',
          teaser: 'Killer Prices. Full Transparency. All Digital.'
        },
        why: {
          title: 'Why Simpego?',
          teaser: 'We have already made the comparison for you and therefore only offer the insurances with the best price-to-value ratio.'
        }
      },
      de: {
        hero: {
          title: 'Autoversicherung, abgefahren einfach!',
          teaser: 'Unschlagbare Preise. Volle Transparenz. Alles Digital.'
        },
        why: {
          title: 'Warum Simpego?',
          teaser: 'Wir haben bereits für dich verglichen und bieten deshalb nur die Versicherugen mit dem besten Preis-Leistungs-Verhältnis an.'
        }
      }
    }
  }
}
</script>

