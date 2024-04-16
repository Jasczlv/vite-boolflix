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
</template>
<style>
li {
  list-style: none;
}

.ul-style {
  max-width: 600px;
  border: 0.5px solid rgba(0, 0, 0, 0.374);
  padding: 50px;
  background-color: rgba(169, 169, 169, 0.249);
}
</style>
