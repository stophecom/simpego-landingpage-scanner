<template>
  <div v-if="plain" class="button" :class="buttonColor(color)">
    <slot></slot>
  </div>
   <a v-else-if="href" class="button" :class="buttonColor(color)" :href="href" rel="noopener" target="_blank">
    <slot></slot>
  </a>
  <nuxt-link v-else class="button" :class="buttonColor(color)" :to="localePath(to)">
    <slot></slot>
  </nuxt-link>
</template>

<script>
export default {
  props: {
    color: {
      type: String,
      default: 'primary'
    },
    to: {
      type: String,
      default: '/'
    },
    href: {
      type: String,
      default: ''
    },
    plain: {
      type: Boolean,
      default: false
    }
  },

  methods: {
    buttonColor: (color) => ({
      'button--primary': color === 'primary',
      'button--secondary': color === 'secondary',
      'button--transparent': color === 'transparent'
    })
  }
}

</script>

<style lang="scss">
.button {
  align-items: center;
  background-clip: padding-box;
  border-radius: $radius;
  box-shadow: none;
  color: #363636;
  cursor: pointer;
  display: inline-flex;
  height: 2.25em;
  justify-content: center;
  line-height: 1.5;
  font-size: 1rem;
  font-weight: 600;
  margin: 0.2rem;
  padding: calc(0.375em - 1px) 0.75em;
  position: relative;
  user-select: none;
  text-align: center;
  transition: .1s ease-out;
  vertical-align: top;
  white-space: nowrap;
  -webkit-appearance: none;

  @media screen and (min-width: $breakpointSmall) {
    font-size: 1.2rem;
  }

  &:hover {
    box-shadow: 0 2px 8px rgba(0,0,0,.3);
    transform: translateY(-1px);
  }

  &.button--primary {
    background-clip: padding-box;
    background-image: linear-gradient(90deg,#37f267,#0abb72);
    color: #fff;
  }

  &.button--secondary {
    background-color: $secondary;
    color: #fff;
  }

  &.button--transparent {
    background-color: transparent;
    color: $text;
    font-weight: normal;
    font-size: 0.9em;

    &:hover {
      box-shadow: none;
    }
  }
}
</style>
