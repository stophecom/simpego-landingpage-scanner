<template>
  <nav class="header">
    <div class="container header-inner">
      <a class="logo" href="/">
        <img alt="Simpego Logo" src="/images/logo.svg" width="104" height="27">
      </a>
      <span class="tagline">{{ $t('tagline') }}</span>
      <i18n-switcher/>
      <a class="link" aria-current="false" href="https://www.simpego.ch/kontakt/">Feedback</a>
    </div>
  </nav>
</template>

<script>
  export default {
    i18n: {
      messages: {
        en: {
          tagline: 'smart insurance'
        },
        de: {
          tagline: 'smart versichert'
        }
      }
    }
  }
</script>

<style lang="scss">
  .header {
    background-color: $defaultBackground;
    border-bottom: 1px solid $colorBorder;
    height: $header-height;
    left: 0;
    padding-left: $sectionPadding;
    padding-right: $sectionPadding;
    position: fixed;
    right: 0;
    top: 0;
    z-index: 30;

    .header-inner {
      align-items: center;
      display: flex;
      height: 100%;
    }

    .language-switcher {
      display: flex;
      margin-left: auto;
      margin-right: 1em;
      text-transform: uppercase;

      > li {
        &:not(:last-child)::after {
          content: '|';
          opacity: 0.3;
        }

        a {
          color: $text;
          padding: 0.2rem;
        }
      }
    }

    a {
      padding: 0.5rem 0;
    }

    .logo {
      display: flex;
      align-items: center;
    }

    .tagline {
      display: none;
      font-size: 0.8rem;
      margin-left: 1rem;

      @media screen and (min-width: $breakpointMini) {
        display: inline;
      }
    }
  }
</style>
