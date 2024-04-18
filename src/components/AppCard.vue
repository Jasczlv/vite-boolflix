<script>
import { store } from "../store.js";
import "/node_modules/flag-icons/css/flag-icons.min.css";
export default {
  data() {
    return {
      store,
      stelleGenerate: 0,
    };
  },
};
</script>

<template>
  <div class="container-liquid d-flex flex-wrap justify-content-center">
    <div v-for="dati in store.film" class="card d-flex m-3">
      <ul>
        <img
          :src="`https://image.tmdb.org/t/p/w342/${dati.imgPath}`"
          alt="immagine non trovata :("
        />
        <div class="overlay">
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
              <span
                :class="'fi-' + (dati.lang === 'en' ? 'gb' : dati.lang)"
              ></span>
            </div>
          </li>
          <li class="fw-bold">
            voto:
            <font-awesome-icon
              v-for="(stella, i) in dati.stars"
              :key="i"
              :icon="['fas', 'star']"
            />
            <font-awesome-icon
              v-for="(stella, i) in dati.emptyStars"
              :icon="['far', 'star']"
            />
          </li>
        </div>
      </ul>
    </div>
  </div>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
}

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

.overlay {
  background-color: rgba(9, 9, 9, 0.583);
  position: absolute;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  opacity: 0;
  transition: opacity 0.5s ease;
}

.card:hover .overlay {
  opacity: 1;
}

.card {
  position: relative;
  cursor: pointer;
  color: white;
  border: 1px solid rgba(0, 0, 0, 0.374);
  padding: 1.1px !important;
  background-color: rgba(0, 0, 0, 0.714);
}
</style>
