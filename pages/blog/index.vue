<template>
  <div>
    <nuxt-link
      v-for="page in pages"
      :key="page.slug"
      :to="`blog/${page.slug}`"
      >{{ page.slug }}</nuxt-link
    >
  </div>
</template>
<script>
export default {
  name: "Blog",
  data() {
    return {
      pages: []
    };
  },
  async fetch() {
    this.pages = await this.$content()
      .only(["slug"])
      .where({ slug: this.$route.params.slug, extension: ".md" })
      .fetch();
  }
};
</script>
