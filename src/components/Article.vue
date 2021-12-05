<template>
  <li v-if="isVisible">
    <div class="article">
      <button
        type="button"
        class="btn-close btn-close-white"
        aria-label="Close"
        @click="isVisible = false"
      ></button>
      <h3 class="articleTitle">
        <a :href="article.url" target="blank">{{ article.title }}</a>
      </h3>
      <p>
        <b>{{ article.source.name }}</b>
        at {{ article.publishedAt }}
      </p>
      <img class="articleImage" :src="article.urlToImage" />
      <p>{{ article.description }}</p>
    </div>
  </li>
</template>

<script>
export default {
  name: "Article",
  props: ["article"],
  data() {
    return {
      isVisible: true,
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.article {
  margin: 30px 10px;
  padding: 30px 50px;
  border-radius: 10px;
  background: #202020;
  color: azure;
}
button {
  float: right;
}
img {
  width: 40%;
  margin: 10px;
}
a {
  color: #42b983;
}
</style>
