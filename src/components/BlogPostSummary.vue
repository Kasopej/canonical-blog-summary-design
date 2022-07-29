<template>
  <div class="p-card">
    <div class="p-card__content">
      <img
        class="p-card__image"
        alt=""
        height="185"
        width="330"
        :src="blog.featured_media"
      />
      <h4>
        <a href="#">{{ blog.title.rendered }}</a>
      </h4>
      <p class="u-no-padding--bottom">
        By <a class="text-primary">{{ blog._embedded.author[0].name }}</a> on
        {{ formattedDate }}
      </p>
    </div>
    <hr />
    <div class="p-card__content">
      {{ blog.type | capitalize }}
    </div>
  </div>
</template>

<script>
export default {
  name: "BlogPostSummary",
  props: {
    blog: {
      type: Object,
      required: true,
    },
  },
  computed: {
    formattedDate() {
      return `${new Date(this.blog.date).toDateString().slice(4)}`;
    },
  },
  filters: {
    capitalize(string) {
      return string[0].toUpperCase() + string.slice(1);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss"></style>
