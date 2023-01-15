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
      apiURI:
        "https://api.themoviedb.org/3/movie/550?api_key=d6632532f354537ddbd1e734979a4b52",
    };
  },

  methods: {
    //Filtro la ricerca sul valore inserito
    searchContent(value) {
      axios
        .get(this.apiURI, {
          params: {
            query: value,
          },
        })
        .then((response) => {
          this.store.movies = response.results;
          console.log(this.store.movies);
        });
    },
  },

  created() {
    this.searchContent("");
  },
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
