<script>
import axios from "axios";
export default {
  data() {
    return {
      inputValue: "",
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
          for (let i = 0; i < 20; i++) {
            console.log(res);
            const data = res.data.results[i];
            const name = data.title;
            const originalName = data.original_title;
            const lang = data.original_language;
            const rating = data.vote_average;
            const imgPath = data.backdrop_path;
            this.film.push({
              name,
              originalName,
              lang,
              rating,
              imgPath,
            });
            console.log(
              name + ",",
              "nome originale: " + originalName + ",",
              "lingua: " + lang + ",",
              "voto: " + rating
            );
          }
        });
    },
  },
  mounted() {
    this.getApi();
  },
};
</script>
<template>
  <div class="m-5">
    <h1 class="col-auto">Boolflix</h1>
    <div>
      <input type="text" placeholder="Cerca film" v-model="inputValue" />
      <button @click="getApi">send</button>
    </div>

    <ul class="ul-style" v-for="dati in film">
      <img
        :src="`https://image.tmdb.org/t/p/w500${dati.imgPath}`"
        alt="immagine non trovata :("
      />
      <li><span class="fw-bold">nome: </span> {{ dati.name }}</li>
      <li>
        <span class="fw-bold">nome originale: </span> {{ dati.originalName }}
      </li>
      <li><span class="fw-bold">lingua: </span> {{ dati.lang }}</li>
      <li><span class="fw-bold">voto: </span> {{ dati.rating }}</li>
    </ul>
  </div>
</template>
<style scoped>
li {
  list-style: none;
}

.ul-style {
  min-width: 600px;
  border: 0.5px solid rgba(0, 0, 0, 0.374);
  padding: 50px;
  background-color: rgba(169, 169, 169, 0.249);
}

.m-5 {
  max-width: 100%;
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
  margin: 0 auto;
  align-items: center;
  justify-content: center;
}

.m-5 > * {
  margin-bottom: 15px;
}
</style>
