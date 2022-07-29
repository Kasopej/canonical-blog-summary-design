<template>
  <div id="app">
    <BlogPostSummary v-for="blog in blogs" :key="blog.id" />
  </div>
</template>

<script>
import BlogPostSummary from "./components/BlogPostSummary.vue";

export default {
  name: "App",
  components: {
    BlogPostSummary,
  },
  data() {
    return {
      blogs: [],
    };
  },
  methods: {
    async getBlogPosts() {
      this.blogs = await fetch(
        "https://people.canonical.com/~anthonydillon/wp-json/wp/v2/posts.json "
      ).then((res) => res.json());
      console.log(this.blogs);
    },
  },
  created() {
    this.getBlogPosts();
  },
};
</script>

<style lang="scss">
@import "assets/styles/base.scss";
</style>
