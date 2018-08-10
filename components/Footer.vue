<template>
    <footer class="footer">
        <div class="container">
            <nav>
                <ul class="footer__menu">
                    <li class="logo"><a class="active" aria-current="true" alt="Startseite" href="/"><img alt="Simpego Logo" src="/images/logo.svg" width="104" height="27"></a></li>
                    <li><a aria-current="false" href="https://www.simpego.ch/about/">Über Simpego</a></li>
                    <li><a aria-current="false" href="https://www.simpego.ch/faq/">FAQ</a></li>
                    <li><a aria-current="false" href="https://www.simpego.ch/rechtliches/">Rechtliches</a></li>
                    <li><a aria-current="false" href="https://www.simpego.ch/kontakt/">Kontakt</a></li>
                </ul>
            </nav>
            <ul class="footer__trust-badges">
                <li><a href="https://www.finma.ch" rel="noopener noreferrer" target="_blank"><img alt="Logo der Finanzmarktaufsicht (Finma)" src="/images/finma.png" width="107" height="28"></a></li>
                <li><img alt="Diese Seite benutzt SSL-Verschlüsselung" src="/images/ssl-checkmark.png"></li>
            </ul>
        </div>
        <ul class="social-media-links">
            <li><a aria-label="Facebook" href="https://www.facebook.com/simpego" rel="noopener noreferrer" target="_blank"><span class="fa fa-facebook"></span></a></li>
            <li><a aria-label="Twitter" href="https://twitter.com/Simpego_Schweiz" rel="noopener noreferrer" target="_blank"><span class="fa fa-twitter"></span></a></li>
            <li><a aria-label="Instagram" href="https://www.instagram.com/simpego" rel="noopener noreferrer" target="_blank"><span class="fa fa-instagram"></span></a></li>
        </ul>
    </footer>
</template>

<style lang="scss">
.footer {
  background-color: white;
  border-top: 1px solid $colorBorder;
  padding: 1em $sectionPadding;

  a {
    color: $text-strong;
    display: block;
  }

  .container {
    align-items: flex-end;
    display: flex;
    margin-top: 2em;

    @media screen and (min-width: $breakpointSmall) {
      align-items: center;
    }
  }

  &__menu {
    @media screen and (min-width: $breakpointSmall) {
      display: flex;
    }

    a {
      padding: 0.5em;
    }

    .logo {
      margin-right: 1em;
    }
  }

  &__trust-badges {
    display: flex;
    margin-left: auto;

    img {
      object-fit: contain;
      max-height: 1.2rem;
    }
  }

  .social-media-links {
    display: flex;
    justify-content: center;
    margin-top: 1em;

    a {
      font-size: 1.5rem;
      opacity: 0.6;
      padding: 0.4rem;
    }
  }
}

</style>
