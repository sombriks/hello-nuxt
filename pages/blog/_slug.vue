<template>
  <nuxt-content :document="page[0]" />
</template>
<script>
export default {
  data() {
    return {
      page: ""
    };
  },
  async fetch() {
    this.page = await this.$content()
      .where({ extension: ".md" })
      .fetch(); 
  }
};
</script>
