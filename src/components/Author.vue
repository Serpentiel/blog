<template>
  <div class="author">
    <h1 v-if="showTitle" class="author__site-title">
      {{ $static.metadata.siteName }}
    </h1>

    <p class="author__intro">
      {{ $static.metadata.siteDescription }}
    </p>

    <p class="author__links">
      <a href="//github.com/Serpentiel">GitHub</a>
      <a href="//x.com/srpntl">X</a>
    </p>
  </div>
</template>

<static-query>
query {
  metadata {
    siteName
    siteDescription
  }
}
</static-query>

<script>
export default {
  props: ['showTitle'],
}
</script>

<style lang="scss">
.author {
  margin: 0 auto;
  max-width: 500px;
  text-align: center;
  padding: calc(var(--space) / 2) 0;

  &__intro {
    opacity: .8;
  }

  &__site-title {
    font-size: 1.5em;
  }

  &__links {
    margin-top: -.5em;

    a {
      margin: 0 .5em;
    }
  }
}
</style>
