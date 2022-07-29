<template>
  <div id="app" class="row u-equal-height">
    <blog-post-summary
      class="col-4 col-medium-2 col-small-4"
      v-for="blog in blogs"
      :key="blog.id"
      :blog="blog"
    />
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
    },
  },
  created() {
    //fetch blog posts and pass to blogs array which will be used to create components
    this.getBlogPosts();
  },
};
</script>

<style lang="scss">
@import "assets/styles/base.scss";
</style>
