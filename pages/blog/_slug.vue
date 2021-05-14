<template>
  <article>
    <nav>
      <nuxt-link to="/">🏠back to home </nuxt-link>
    </nav>
    <header class="header">
      <h1 class="title">{{ article.title }}</h1>
      <p>{{ formatDate(article.date) }}</p>
    </header>

    <nuxt-content :document="article" />
  </article>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const article = await $content('articles', params.slug).fetch()

    return { article }
  },
  methods: {
    formatDate(date) {
      return new Date(date).toDateString()
    },
  },
}
</script>

<style>
.header {
  margin: 2rem 0;
}
.title {
  font-size: 2.5rem;
  margin-bottom: 1rem;
  text-decoration: underline;
}

.nuxt-content > * {
  margin: 1.5rem 0;
}
.nuxt-content h2 {
  font-weight: bold;
  font-size: 28px;
}
.nuxt-content h3 {
  font-weight: bold;
  font-size: 22px;
}
.nuxt-content p,
li {
  line-height: 1.3rem;
}

.nuxt-content li {
  margin: 0.6rem 1.5rem;
}
.nuxt-content img {
  max-width: 100%;
}
</style>
