<template>
  <Layout>
    <div class="post-title">
      <h1 class="post-title__text">
        {{ $page.post.title }}
      </h1>

      <PostMeta :post="$page.post"/>

    </div>

    <div class="post content-box">
      <div class="post__header">
        <g-image v-if="$page.post.cover_image" :src="$page.post.cover_image"/>
      </div>

      <div class="post__content" v-html="$page.post.content"/>

      <div class="post__footer">
        <PostTags :post="$page.post"/>
      </div>
    </div>

    <div class="post-comments">
      <script
          type="application/javascript"
          src="https://giscus.app/client.js"
          data-repo="Serpentiel/blog"
          data-repo-id="MDEwOlJlcG9zaXRvcnkzMzgxODU3OTU="
          data-category="Post Comments"
          data-category-id="MDE4OkRpc2N1c3Npb25DYXRlZ29yeTMzMDc2Nzcy"
          data-mapping="pathname"
          data-reactions-enabled="1"
          crossorigin="anonymous"
          async
          :key="giscusTheme"
          :data-theme="giscusTheme"
      >
      </script>
    </div>
  </Layout>
</template>

<script>
import PostMeta from '~/components/PostMeta'
import PostTags from '~/components/PostTags'

export default {
  components: {
    PostMeta,
    PostTags,
  },
  metaInfo() {
    return {
      title: this.$page.post.title,
      meta: [
        {
          name: 'description',
          content: this.$page.post.description
        },
      ],
    }
  },
  computed: {
    giscusTheme: function () {
      return window.__theme === 'dark' ? 'dark_dimmed' : 'light';
    }
  },
}
</script>

<page-query>
query Post ($id: ID!) {
  post: post (id: $id) {
    title
    path
    date (format: "MMMM D, YYYY")
    timeToRead
    tags {
      id
      title
      path
    }
    description
    content
    # cover_image (width: 860, blur: 10)
  }
}
</page-query>

<style lang="scss">
.post-title {
  padding: calc(var(--space) / 2) 0 calc(var(--space) / 2);
  text-align: center;
}

.post {
  &__header {
    width: calc(100% + var(--space) * 2);
    margin-left: calc(var(--space) * -1);
    margin-top: calc(var(--space) * -1);
    margin-bottom: calc(var(--space) / 2);
    overflow: hidden;
    border-radius: var(--radius) var(--radius) 0 0;

    img {
      width: 100%;
    }

    &:empty {
      display: none;
    }
  }

  &__content {
    h2:first-child {
      margin-top: 0;
    }

    p:first-of-type {
      font-size: 1.2em;
      color: var(--title-color);
    }

    img {
      width: calc(100% + var(--space) * 2);
      margin-left: calc(var(--space) * -1);
      display: block;
      max-width: none;
    }
  }
}

.post-comments {
  padding: calc(var(--space) / 2);
  max-width: var(--content-width);
  margin: 0 auto;
}

.post-author {
  margin-top: calc(var(--space) / 2);
}
</style>
