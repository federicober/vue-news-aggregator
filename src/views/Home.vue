<template>
  <div class="home">
    <ul>
      <Article
        v-for="article in articles"
        :key="article.url"
        :article="article"
      />
    </ul>
  </div>
</template>

<script>
// @ is an alias to /src
import Article from "@/components/Article.vue";
import Config from "../config.json";

export default {
  name: "Home",
  data() {
    return {
      articles: [],
    };
  },
  components: {
    Article,
  },
  async mounted() {
    let response = await fetch(
      "https://newsapi.org/v2/top-headlines?q=bitcoin&sortBy=popularity&apiKey=" +
        Config.newsApiKey
    );
    // TODO Add error handling
    let payload = await response.json();
    this.articles = payload.articles;
  },
};
</script>

<style scoped>
ul {
  column-count: 2;
  columns: 2;
  -webkit-columns: 2;
  -moz-columns: 2;
  margin: 0;
  list-style-type: none; /* Remove bullets */
  padding: 0; /* Remove padding */
  margin: 0; /* Remove margins */
}
</style>
