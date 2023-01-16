<script>
//Importo Axios per recuperare i dati dall'API
import axios from "axios";
//Collego lo StoreJS che raccoglie le chiamate fatta all'API
import { store } from "./store.js";

//Importo i Componenti figli
import HeaderApp from "./components/HeaderApp.vue";
import MainApp from "./components/MainApp.vue";

export default {
  components: {
    HeaderApp,
    MainApp,
  },
  data() {
    return {
      store,
      apiKey: "d6632532f354537ddbd1e734979a4b52",
      moviesApi: "https://api.themoviedb.org/3/search/movie",
      seriesApi: "https://api.themoviedb.org/3/search/tv",
    };
  },

  methods: {
    //MILESTONE 1 - RICERCA FILM
    //Filtro la ricerca sul valore inserito
    // searchContent(value) {
    //   axios
    //     .get(this.moviesApi, {
    //       params: {
    //         api_key: this.apiKey,
    //         query: value,
    //       },
    //     })
    //     .then((response) => {
    //       this.store.moviesList = response.data.results;
    //       console.log(this.store.moviesList);
    //     });
    // },

    //MILESTONE 2 - Ricerca Film e Serie Tv
    searchContent(value) {
      const movieResponse = axios.get(this.moviesApi, {
        params: {
          api_key: this.apiKey,
          query: value,
        },
      });
      const seriesResponse = axios.get(this.seriesApi, {
        params: {
          api_key: this.apiKey,
          query: value,
        },
      });

      axios
        .all([movieResponse, seriesResponse])
        .then(
          axios.spread((...responses) => {
            this.store.moviesList = responses[0].data.results;
            this.store.seriesList = responses[1].data.results;
          })
        )
        .catch((errors) => {
          console.log(errors);
        });
    },
  },

  // created() {
  //   this.searchContent("");
  // },
};
</script>

<template>
  <header>
    <HeaderApp @search="searchContent" />
  </header>
  <main>
    <MainApp />
  </main>
</template>

<style lang="scss">
@use "./assets/styles/general.scss";
</style>
