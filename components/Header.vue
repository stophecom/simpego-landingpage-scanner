<template>
    <nav class="header">
        <div class="container header-inner">
            <a class="logo" href="/">
                      <img alt="Simpego Logo" src="/images/logo.svg" width="104" height="27">
                    </a>
            <span class="tagline">smart versichert</span>
            <a class="link" aria-current="false" href="https://www.simpego.ch/kontakt/">Feedback</a>
        </div>
    </nav>
</template>

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
    .link {
        margin-left: auto;
    }
}
</style>
