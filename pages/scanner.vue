<template>
<div class="scanner">
  <Section>
    <h1>Spare 500 CHF  pro Jahr mit einem Foto.</h1>
    <div class="section__headline">Finde die beste Autoversicherung auf dem gesamten Schweizer Markt. Ein Foto von deinem Fahrzeugausweis genügt. So funktionierts:</div>
    <ul class="manual">
      <li>
        <img alt="Scanner" src="/images/scan.svg" />
        <div class="description"><strong>1.</strong> Fahrzeugausweis fotografieren</div>
      </li>
      <li>
        <img alt="Done" src="/images/done.svg" />
        <div class="description"><strong><del>2.</del> Boom.</strong> Simpege liefert dir das beste Angebot.</div>
      </li>
    </ul>
    <div class="section__cta">
      <Button color="primary">Jetzt scannen</Button>
      <Button color="transparent">Foto hochladen</Button>
    </div>
  </Section>
  </div>
</template>

<script>
import Button from '../components/Button'
import Section from '../components/Section'

export default {
  components: {
    Button,
    Section
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
