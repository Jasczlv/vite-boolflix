<script>
import axios from "axios";
export default {
  data() {
    return {
      inputValue: "ritorno al futuro",
      film: [],
    };
  },
  methods: {
    getApi() {
      axios
        .get(
          `https://api.themoviedb.org/3/search/movie?api_key=a9f93794d83843cad47d4bcbc4f86888&query=${this.inputValue}`
        )
        .then((res) => {
          console.log(res);
          const data = res.data.results[0];
          const name = data.title;
          const originalName = data.original_title;
          const lang = data.original_language;
          const rating = data.vote_average;
          this.film.push({
            name,
            originalName,
            lang,
            rating,
          });
          console.log(
            name + ",",
            "nome originale: " + originalName + ",",
            "lingua: " + lang + ",",
            "voto: " + rating
          );
        });
    },
  },
  mounted() {
    this.getApi();
  },
};
</script>
<template>
  <h1>Boolflix</h1>
  <input type="text" placeholder="Cerca film" v-model="inputValue" />
  <button @click="getApi">send</button>
  <ul v-for="dati in film">
    <li>nome: {{ dati.name }}</li>
    <li>nome originale: {{ dati.originalName }}</li>
    <li>lingua: {{ dati.lang }}</li>
    <li>voto: {{ dati.rating }}</li>
  </ul>
</template>
<style>
li {
  list-style: none;
}
</style>
