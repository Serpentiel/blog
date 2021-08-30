<template>
  <div class="post-tags">
    <g-link class="post-tags__link" v-for="tag in post.tags" :key="tag.id" :to="tag.path">
      <span>#</span> {{ tag.title }}
    </g-link>
  </div>
</template>

<script>
export default {
  props: ['post'],
}
</script>

<style lang="scss">
@import '../assets/style/variables';

.post-tags {
  display: flex;
  flex-wrap: wrap;
  margin-top: 0.5em;

  &__link {
    display: flex;
    margin: 0.5em .7em 0 0;
    font-size: .8em;
    text-decoration: none;
    background-color: var(--bg-color);
    color: currentColor !important;
    padding: .5em;
    border-radius: var(--radius);
  }

  @media screen and (max-width: $sw-sm) {
    justify-content: center;
  }
}
</style>
