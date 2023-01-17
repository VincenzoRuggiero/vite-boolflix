<script>
import { store } from "../store";

export default {
  name: "MediaCard",
  props: ["title", "originalTitle", "lang", "vote", "poster"], //Ricevo i props
  data() {
    return {
      store,
      flags: ["de", "en", "es", "fr", "it", "ja", "pt"], //La lingua originale viene visualizzata con le bandiere, se disponibili.
    };
  },
  methods: {
    getImagePath(image) {
      return new URL(`../assets/images/${image}`, import.meta.url).href; //Funzione che imposta la bandiera in base alla lingua originale del contenuto.
    },
  },
};
</script>

<template>
  <div class="card">
    <img :src="poster" :alt="title" />
    <h2>
      {{ title }}
    </h2>

    <p>{{ originalTitle }}</p>
    <p>Lingua originale:</p>
    <img
      :src="getImagePath(`${lang}_flag.png`)"
      :alt="`${lang} flag`"
      v-if="flags.includes(lang)" />
    <p v-else>{{ lang }}</p>

    <!-- Mostro le stelle in base al voto medio -->
    <fa v-for="i in vote" :key="i" icon="fa-star fa-solid" />
  </div>
</template>

<style lang="scss"></style>
