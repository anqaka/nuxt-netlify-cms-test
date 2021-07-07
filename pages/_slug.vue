<template>
  <div class="p-10 mx-auto max-w-screen-lg">
    <h1 class="text-5xl font-black mb-4">
      {{ post.title }}
    </h1>
    <nuxt-content :document="post" />
    <nuxt-link
      to="/"
      class="block text-green-700 underline font-bold items-center mt-4"
    >
      Back to list
    </nuxt-link>
  </div>
</template>
<script>
export default {
  async asyncData ({ $content, params, error }) {
    let post
    try {
      post = await $content('blog', params.slug).fetch()
    } catch (e) {
      error({ message: 'Blog Post not found' })
    }

    return {
      post
    }
  }
}
</script>
