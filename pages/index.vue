<template>
  <article class="main-article">
    <section v-for="article in articles" :key="article.title">
      <article class="article">
        <header>
          <h4>
            <nuxt-link :to="`blog/${article.slug}`">
              {{ article.title }}
            </nuxt-link>
          </h4>
          <!-- <date>{{ readableDate(article.createdAt) }}</date> -->
          <p class="date">
            {{ readableDate(article.date) }}
          </p>
        </header>
        <p>{{ article.description }}</p>
      </article>
    </section>
  </article>
</template>

<script>
export default {
  data() {
    return {
      articles: [],
    }
  },

  async fetch() {
    this.articles = await this.$content('articles')
      .only(['title', 'description', 'slug', 'date'])
      .sortBy('date', 'desc')
      .fetch()
  },
  methods: {
    readableDate(date) {
      return new Date(date).toDateString()
    },
  },
}
</script>

<style scoped>
.article {
  margin: 2.6rem 0;
}
.article header h4 {
  margin-bottom: 0.5rem;
  font-size: 1.5rem;
  color: rgb(69, 143, 240);
}
.article > * {
  margin: 0.7rem 0;
}
</style>
