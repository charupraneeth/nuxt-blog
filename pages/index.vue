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
          <date v-if="article.createdAt != article.updatedAt">
            {{ readableDate(article.updatedAt) }}
          </date>
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
      .only(['title', 'description', 'createdAt', 'updatedAt', 'slug'])
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
  font-size: 1.5rem;
  color: rgb(69, 143, 240);
}
.article > * {
  margin: 0.7rem 0;
}

a,
a:visited {
  text-decoration: none;
  color: inherit;
}

a:hover {
  color: rgb(37, 93, 167);
}
</style>
