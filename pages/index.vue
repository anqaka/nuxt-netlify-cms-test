<template>
  <section class="text-gray-600 body-font">
    <div class="container px-5 py-24 mx-auto">
      <h1 class="text-5xl font-black mb-4 text-green-900">
        Articles
      </h1>
      <ul class="flex flex-wrap">
        <li
          v-for="post in posts"
          :key="post.slug"
          class="py-8 px-4 lg:w-1/3"
        >
          <div class="h-full flex items-start">
            <div class="flex-grow pl-6">
              <h2 class="title-font text-xl font-medium text-gray-900 mb-3">
                {{ post.title }}
              </h2>
              <p class="leading-relaxed mb-5">
                {{ post.description }}
              </p>
              <nuxt-link
                :to="post.slug"
                class="text-green-700 inline-flex font-bold underline items-center mt-4"
              >
                Read more
              </nuxt-link>
            </div>
          </div>
        </li>
      </ul>
    </div>
  </section>
</template>

<script>
export default {
  async asyncData ({ $content }) {
    const posts = await $content('blog').fetch()
    return {
      posts
    }
  },
  head () {
    return {
      script: [{ src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }]
    }
  }
}
</script>
