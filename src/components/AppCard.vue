<script>
import { store } from "../store.js";
import "/node_modules/flag-icons/css/flag-icons.min.css";
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
    <li>
      <span class="fw-bold">{{ dati.type }} </span>
    </li>
    <li><span class="fw-bold">nome: </span> {{ dati.name }}</li>
    <li v-if="dati.originalName !== dati.name ? true : false">
      <span class="fw-bold">nome originale: </span>
      {{ dati.originalName === dati.name ? "" : dati.originalName }}
    </li>
    <li class="language-li">
      <div>
        <span class="fw-bold">lingua: </span>
        <span>{{ dati.lang }} </span>
        <span :class="'fi-' + (dati.lang === 'en' ? 'gb' : dati.lang)"></span>
      </div>
    </li>
    <li class="fw-bold">
      voto:
      <span v-for="(stella, i) in dati.stars">
        <font-awesome-icon :icon="['fas', 'star']" />
      </span>
    </li>
  </ul>
</template>

<style>
li {
  list-style: none;
}

[class^="fi-"] {
  display: inline-block;
  width: 30px;
  aspect-ratio: 3 / 2; /* Aspect ratio di 3:2 */
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
}

.ul-style {
  color: white;
  max-width: 600px;
  border: 0.5px solid rgba(0, 0, 0, 0.374);
  padding: 50px;
  background-color: rgba(0, 0, 0, 0.714);
}
</style>
