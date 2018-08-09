<template>
<div class="index">
  <Hero backgroundImage="/images/background-car-3.jpg">
    <h1>Autoversicherung, abgefahren einfach!</h1>
    <p>Unschlagbare Preise. Volle Transparenz. Alles Digital.</p>
    <Button color="primary">Jetzt berechnen</Button>
  </Hero>
  <Section>
    <h1>Spare 500 CHF  pro Jahr mit einem Foto.</h1>
    <div class="section__headline">Finde die beste Autoversicherung auf dem gesamten Schweizer Markt. Ein Foto von deinem Fahrzeugausweis genügt.</div>
    <div class="section__cta">
      <Button color="primary">Jetzt scannen</Button>
    </div>
  </Section>
  <Section alternative>
    <h2>Warum Simpego</h2>
    <div class="section__headline">Wir haben bereits verglichen und bieten nur die preiswerten Versicherugen mit dem besten Preis-Leistungs-Verhältnis an.</div>
    <PartnerLogos/>
    <div class="section__cta">
      <Button color="secondary">Mehr erfahren</Button>
    </div>
  </Section>
  </div>
</template>

<script>
import Button from '../components/Button'
import Hero from '../components/Hero'
import Section from '../components/Section'
import PartnerLogos from '../components/PartnerLogos'

export default {
  components: {
    Button,
    Hero,
    Section,
    PartnerLogos
  }
}
</script>

<style lang="scss">

</style>
