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
  <!-- Le card vengono generate dinamicamente con i dati dello store -->
  <div class="cards-wrapper">
    <div class="cards" v-for="show in store.movies">
      <!-- Uso i Props per mandare i dati al componente figlio -->
      <MovieCard
        :title="show.title"
        :originalTitle="show.original_title"
        :lang="show.original_language"
        :vote="show.vote_average" />
    </div>
  </div>
</template>

<style lang="scss"></style>
