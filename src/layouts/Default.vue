<template>
  <div id="app">

    <header class="header">
      <div class="header__left">
        <Logo v-if="showLogo"/>
      </div>

      <div class="header__right">
        <ToggleTheme @themeToggled="$emit('themeToggled')"/>
      </div>
    </header>

    <main class="main">
      <slot/>
    </main>

    <footer class="footer">
      <span class="footer__copyright">Made with &#9825; by Serpentiel</span>
      <span class="footer__links">Powered by <a href="//gridsome.org">Gridsome</a></span>
    </footer>
  </div>
</template>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>

<script>
import Logo from '~/components/Logo.vue'
import ToggleTheme from '~/components/ToggleTheme.vue'

export default {
  props: {
    showLogo: { default: true },
  },
  components: {
    Logo,
    ToggleTheme,
  },
  metaInfo() {
    return {
      titleTemplate: (titleChunk) => {
        let siteName = this.$static.metadata.siteName
        return titleChunk ? `${titleChunk} - ${siteName}` : siteName
      },
    }
  },
}
</script>

<style lang="scss">
@import '../assets/style/variables';

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  min-height: var(--header-height);
  padding: 0 calc(var(--space) / 2);
  top: 0;
  z-index: 10;

  &__left,
  &__right {
    display: flex;
    align-items: center;
  }

  @media screen and (min-width: $sw-xl) {
    position: sticky;
    width: 100%;
  }
}

.main {
  margin: 0 auto;
  padding: 1.5vw 15px 0;
}

.footer {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: calc(var(--space) / 2);
  text-align: center;
  font-size: .8em;

  > span {
    margin: .35em 0 .35em 0;
  }

  a {
    color: currentColor;
  }
}
</style>
