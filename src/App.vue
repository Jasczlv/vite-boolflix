<script>
import AppSearchbar from "./components/AppSearchbar.vue";
import { store } from "./store.js";
import axios from "axios";
export default {
  components: {
    AppSearchbar,
  },
  data() {
    return {
      store,
    };
  },
  methods: {
    getApi() {
      store.film = [];
      axios
        .get(
          `https://api.themoviedb.org/3/search/movie?api_key=a9f93794d83843cad47d4bcbc4f86888&query=${store.inputValue}`
        )
        .then((res) => {
          for (let i = 0; i < res.data.results.length; i++) {
            console.log(res);
            const data = res.data.results[i];
            const name = data.title;
            const type = "Film";
            const originalName = data.original_title;
            const lang = data.original_language;
            const rating = data.vote_average;
            const imgPath = data.backdrop_path;
            store.film.push({
              name,
              type,
              originalName,
              lang,
              rating,
              imgPath,
            });
          }
        });

      axios
        .get(
          `https://api.themoviedb.org/3/search/tv?api_key=a9f93794d83843cad47d4bcbc4f86888&query=${store.inputValue}`
        )
        .then((res) => {
          for (let i = 0; i < res.data.results.length; i++) {
            console.log(res);
            const data = res.data.results[i];
            const name = data.title;
            const type = "Serie Tv";
            const originalName = data.original_title;
            const lang = data.original_language;
            const rating = data.vote_average;
            const imgPath = data.backdrop_path;
            store.film.push({
              name,
              type,
              originalName,
              lang,
              rating,
              imgPath,
            });
          }
        });
    },
  },
};
</script>
<template>
  <AppSearchbar @search="getApi" />
</template>
<style></style>
