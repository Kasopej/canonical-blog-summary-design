<template>
  <div class="p-card p-card--highlighted branded-border">
    <div class="p-card__content u-no-padding--top" style="font-size: 0.9rem">
      {{ blog._embedded["wp:term"][1][0].name.toUpperCase() }}
    </div>
    <hr />
    <div class="p-card__content">
      <img
        class="p-card__image"
        alt=""
        height="185"
        width="330"
        :src="blog.featured_media"
      />
      <div class="fix-height">
        <a class="text-primary p-heading--3">{{ blog.title.rendered }}</a>
      </div>
      <p class="author">
        By
        <a class="text-primary">{{ blog._embedded.author[0].name }}</a>
        on
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
