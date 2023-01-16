<script>
import { store } from "../store";
import MediaCard from "./MediaCard.vue";

export default {
  name: "MainApp",
  components: {
    MediaCard,
  },

  data() {
    return {
      store,
      basePosterUrl: "https://image.tmdb.org/t/p/w300", //MILESTONE 3 - Copertine di Film e Serie Tv
    };
  },
};
</script>

<template>
  <!-- Le card vengono generate dinamicamente con i dati dello store -->
  <div class="cards-wrapper">
    <div class="cards" v-for="show in store.moviesList">
      <!-- Uso i Props per mandare i dati al componente figlio -->
      <MediaCard
        :poster="`${this.basePosterUrl}` + show.poster_path"
        :title="show.title"
        :originalTitle="show.original_title"
        :lang="show.original_language"
        :vote="show.vote_average" />
    </div>

    <div class="cards" v-for="show in store.seriesList">
      <!-- Uso i Props per mandare i dati al componente figlio -->
      <MediaCard
        :poster="`${this.basePosterUrl}` + show.poster_path"
        :title="show.name"
        :originalTitle="show.name"
        :lang="show.original_language"
        :vote="show.vote_average" />
    </div>
  </div>
</template>

<style lang="scss"></style>
