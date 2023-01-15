<script>
import { store } from "../store";
import MovieCard from "./MovieCard.vue";

export default {
  name: "MainApp",
  components: {
    MovieCard,
  },

  data() {
    return {
      store,
    };
  },
};
</script>

<template>
  <div class="movie-cards">
    <MovieCard />
  </div>
</template>

<style lang="scss"></style>
