<script>
import { store } from "../store.js";
export default {
  data() {
    return {
      store,
    };
  },
};
</script>
<template>
  <div class="m-5">
    <h1 class="col-auto">Boolflix</h1>
    <div>
      <input type="text" placeholder="Cerca film" v-model="store.inputValue" />
      <button @click="$emit('search')">send</button>
    </div>

    <ul class="ul-style" v-for="dati in store.film">
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
