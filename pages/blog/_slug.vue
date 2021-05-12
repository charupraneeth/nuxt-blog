<template>
  <article>
    <nav>
      <nuxt-link to="/">Home</nuxt-link>
    </nav>
    <header class="header">
      <h1 class="title">{{ article.title }}</h1>
      <date>{{ article.updatedAt }}</date>
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
      return new Date(date).toLocaleString()
    },
  },
}
</script>

<style>
.header {
  margin: 2rem 0;
}
.title {
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
.nuxt-content p {
  margin-bottom: 20px;
}
.nuxt-content img {
  max-width: 100%;
}
</style>
