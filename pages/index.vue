<template>
  <section class="container">
    <div>
      ``
      <logo />
      <h1 class="title">
        cms-frontend
      </h1>
      <div
        v-for="(page, i) in pages"
        :key="i"
        class="bg-purple text-white px-6 py-6 mb-5"
      >
        <h1>{{ page.Title }}</h1>
        <p>{{ page.Content }}</p>
      </div>
    </div>
  </section>
</template>

<script>
import Logo from '~/components/Logo.vue'

export default {
  components: {
    Logo
  },
  data() {
    return {
      pages: []
    }
  },
  async fetch() {
    this.pages = await this.$axios
      .get('http://localhost:1337/pages')
      .then(res => res.data)
  },
  fetchOnService: false
}
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
  @apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
