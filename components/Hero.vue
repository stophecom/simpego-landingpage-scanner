<template>
    <section class="hero">
        <img alt="Background" class="hero__background" :src="backgroundImage" />
        <div class="hero__content">
          <slot></slot>
        </div>
        <span class="more fa fa-arrow-down"></span>
    </section>
</template>

<script>
export default {
  props: {
    backgroundImage: {
      type: String,
      default: '/images/background-drones.jpg'
    }
  }
}
</script>

<style lang="scss">
.hero {
    align-items: center;
    display: flex;
    justify-content: center;
    min-height: calc(100vh - #{$header-height});
    position: relative;

    @media screen and (min-width: $breakpointMini) {
      min-height: calc(100vh - #{$header-height});
    }

    .hero__background {
        left: 0;
        height: 100%;
        object-fit: cover;
        position: absolute;
        top: 0;
        width: 100%;
    }

    &::after {
        background-color: rgba(0, 0, 0, 0.2);
        content: '';
        left: 0;
        height: 100%;
        position: absolute;
        top: 0;
        width: 100%;
    }

    .more {
      bottom: 3vh;
      color: rgba(255, 255, 255, 0.5);
      font-size: 1rem;
      left: 50%;
      position: absolute;
      transform: translateX(-50%);
      z-index: 1;
    }

    .hero__content {
      color: white;
      position: relative;
      max-width: 90%;
      z-index: 1;
      text-align: center;
      text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.12);
      margin-top: 10vh;

      @media screen and (min-width: $breakpointMini) {
        max-width: 80%;
      }

      @media screen and (min-width: $breakpointSmall) {
        max-width: 580px;
      }

      @media screen and (min-width: $breakpointMedium) {
        max-width: 700px;
      }

      h1 {
        font-size: 1.8rem;
        margin-bottom: 0.4em;

        @media screen and (min-width: $breakpointSmall) {
          font-size: 3rem;
        }

        @media screen and (min-width: $breakpointMedium) {
          font-size: 4rem;
        }
      }

      p {
        font-size: 1rem;
        font-weight: 600;
        margin-bottom: 2em;

        @media screen and (min-width: $breakpointSmall) {
          font-size: 1.2rem;
        }
      }

      .button {
        transform: scale(1.2);
      }
    }
}
</style>
